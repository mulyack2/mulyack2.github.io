---
title: KakaoTalk-OpenChat_Analysis-EDA/Statistical-Analysis
date: 2024-03-02
categories: [Project, OpenChat_Analysis]
tags: [Programming, Python]
---

## KakaoTalk-OpenChat_Analysis Series

- [KakaoTalk-OpenChat_Analysis-BluePrint](/posts/open_chat_analysis-blueprint/)
- [KakaoTalk-OpenChat_Analysis-eda_statistics](/posts/open_chat_analysis-eda_statistics/)
- [KakaoTalk-OpenChat_Analysis-ml](/posts/open_chat_analysis-ml/)
- [KakaoTalk-OpenChat_Analysis-DL](/posts/open_chat_analysis-dl/)

---

## EDA / Statistical Analysis

채팅 데이터 EDA 및 간단한 통계분석

## 작업사항

---

### 0. 전처리

전처리에서 체크할 것

1. 채팅 봇의 제거
1. macro 채팅에 대한 제거
1. 모든 채팅 데이터를 사용할 것 vs 최소 n회 이상의 대화가 있는 유저의 데이터를 사용할 것

### 1. EDA

![image](/assets/img/_posts/project/open_chat_analysis/01_eda.png)

---

### 2. Statistical Analysis

#### 2.1 유저별 채팅 비율

- 채팅방에서 top n의 채팅량을 가진 유저는 누구?

#### 2.2 유저별 평균 채팅 길이

- 채팅방에서 top n의 평균 채팅길이를 가진 유저는 누구?

#### 2.3 특정 Argument 비율

- 채팅방에서 `argument` 사용 비율이 높은 유저는 누구?
  - ex) `emoticon` / `ㅋㅋ` ...

```python
class StatsController:
    def __init__(self, df) -> None:
        self.df = df

    def user_chat_ratio(self, top_n=None, recent_n=None):
        df = self.df.copy()
        if recent_n:
            df = df.tail(recent_n)
        ucr_df = df.groupby("User").size() / len(df)

        if top_n:
            ucr_df = ucr_df.nlargest(top_n)
            ucr_df = pd.concat([ucr_df, pd.Series({"etc": 1 - ucr_df.sum()})])
        return ucr_df.to_frame("ratio")

    def user_len_ratio(self, top_n=None, recent_n=None):
        df = self.df.copy()
        if recent_n:
            df = df.tail(recent_n)

        len_df = pd.concat([df["User"], df["Message"].apply(len)], axis=1)
        ulr_df = (
            len_df.groupby("User")["Message"].sum() / len_df["Message"].sum()
        )
        if top_n:
            ulr_df = ulr_df.nlargest(top_n)
            ulr_df = pd.concat([ulr_df, pd.Series({"etc": 1 - ulr_df.sum()})])
        return ulr_df.to_frame("ratio")

    def user_arg_ratio(self, arg, recent_n=None):
        df = self.df
        if recent_n:
            df = df.tail(recent_n)
        filtered_df = df[df["Message"].str.contains(arg)]
        ratio_series = (
            filtered_df.groupby("User").size() / df.groupby("User").size()
        ).dropna()
        ratio_df = ratio_series.to_frame(name="ratio")
        return ratio_df

```
