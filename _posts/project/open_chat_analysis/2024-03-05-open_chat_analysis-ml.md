---
title: KakaoTalk-OpenChat_Analysis-ML
date: 2024-03-05
categories: [Project, OpenChat_Analysis]
tags: [_All, NLP]
---

## KakaoTalk-OpenChat_Analysis Series

- [KakaoTalk-OpenChat_Analysis-BluePrint](/posts/open_chat_analysis-blueprint/)
- [KakaoTalk-OpenChat_Analysis-eda_statistics](/posts/open_chat_analysis-eda_statistics/)
- [KakaoTalk-OpenChat_Analysis-ml](/posts/open_chat_analysis-ml/)
- [KakaoTalk-OpenChat_Analysis-DL](/posts/open_chat_analysis-dl/)

---

## ML (관계분석)

채팅 데이터를 통한 유저 관계 분석

---

## 작업사항

### 1. 채팅 데이터의 Session 생성

|    | Date                | Message      |
|---:|:--------------------|:-------------|
|  2 | 2024-03-15 08:02:45 | im back      |
|  3 | 2024-03-15 08:04:26 | 포션님 하위  |
|  4 | 2024-03-15 08:04:48 | Hello        |
|  5 | 2024-03-15 08:09:13 | 이게맞는걸까 |
|  6 | 2024-03-15 08:10:56 | 하이포션     |

#### 1.1 time_limit based session 구분

- n시간 이상 대화가 멈추면 session 종료

#### 1.2 volume_limit based session 구분

- n시간 동안 / m회 이상의 대화가 있다면 session으로 인정 나머지 종료

#### 1.3 time_series_clutsering based session 구분

- 밀도를 기반으로 session을 분리
- using DBSCAN

---

### 2. Session 기반의 관계 분석

#### 2.1 Absoulte score

- 절대적인 관계 score
  - 누가 나와 같은 session에서 많이 대화 했나?

#### 2.1 Relative score

- 상대적인 관계 score
  - session 참여 대비 나와 함께 대화한 유저는 누구인가?

> ps
>
> - 친밀도가 같다면
>   - 친구가 한명인 best friend
>   - 친구가 10명인 best friend

```py
class RelationController:
    def __init__(self, session_df) -> None:
        self.df = session_df

    def calc_abs_score(self):
        """User가 참여한 Session 중 Session에 참여한 비율"""
        df = self.df.copy()
        users = set(df["User"])
        absolute_ratio_df = pd.concat(
            [
                self._calc_abs_user_ratio(
                    df, user, self._get_involved_sessions(df, user)
                )
                for user in users
            ],
            axis=1,
        )
        return absolute_ratio_df

    def calc_rel_score(self):
        """전체 참여 Session 중 User가 참여한 Session에 참여한 비율"""
        session_df = self.df.copy()
        users = set(session_df["User"])
        relative_ratio_df = pd.concat(
            [
                self._calc_rel_user_ratio(
                    session_df,
                    user,
                    self._get_involved_sessions(session_df, user),
                )
                for user in users
            ],
            axis=1,
        )
        return relative_ratio_df
```
