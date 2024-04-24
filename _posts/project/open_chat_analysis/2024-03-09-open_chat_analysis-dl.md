---
title: KakaoTalk-OpenChat_Analysis-DL
date: 2024-03-09
categories: [Project, OpenChat_Analysis]
tags: [_All, NLP]
---

## KakaoTalk-OpenChat_Analysis Series

- [KakaoTalk-OpenChat_Analysis-BluePrint](/posts/open_chat_analysis-blueprint/)
- [KakaoTalk-OpenChat_Analysis-eda_statistics](/posts/open_chat_analysis-eda_statistics/)
- [KakaoTalk-OpenChat_Analysis-ml](/posts/open_chat_analysis-ml/)
- [KakaoTalk-OpenChat_Analysis-DL](/posts/open_chat_analysis-dl/)

---

## DL (감성분석)

채팅 데이터를 통한 유저 감성 분석

## 작업사항

### 1. Naver Clova Sentimental Analysis

직접 감성분석을 진행하기에 비용이 좀 많이 들어가서 `API` 로 대체</br>
(월 1000회 무료.)

```py
class NaverAIExtractor:
    def __init__(self, naver_ai_private) -> None:
        self.header = self.__set_header(naver_ai_private)

    def extract_sentimental(self, content):
        base_url = "https://naveropenapi.apigw.ntruss.com/sentiment-analysis/v1/analyze"
        body = self.__get_sentimental_body(content)
        resp = requests.post(
            url=base_url, headers=self.header, data=json.dumps(body)
        )
        return resp.json()

    def __get_sentimental_body(self, content):
        body = {
            "content": "",
        }
        body["content"] = content
        return body

    def extract_summary(self, content):
        base_url = (
            "https://naveropenapi.apigw.ntruss.com/text-summary/v1/summarize"
        )
        body = self.__get_summary_body(content)
        resp = requests.post(
            url=base_url, headers=self.header, data=json.dumps(body)
        )
        return resp.json()

    def __get_summary_body(self, content):
        body = {
            "document": {
                "content": {},
            },
            "option": {
                "language": "ko",
                "model": "general",
                "tone": 0,
                "summaryCount": 3,
            },
        }
        body["document"]["content"] = content
        return body

    def __set_header(self, naver_ai_private):
        header = {
            "X-NCP-APIGW-API-KEY-ID": naver_ai_private["client_id"],
            "X-NCP-APIGW-API-KEY": naver_ai_private["client_secret"],
            "Content-Type": naver_ai_private["content_type"],
        }
        return header
```

### 2. Sentimental Analysis

#### 2.1 Absolute Sentimental

감성분석의 절댓값을 파악하고 / 채팅방 전체의 감성을 파악할 필요가 있다.
왜냐하면 유저의 감성분석 결과가 기본적으로 채팅방의 감성을 따라가기 때문

- 유저 감성분석 결과를 채팅방의 감성분석 결과로 정규화 해야 유저별 적절한 감성을 파악가능

#### 2.2 Relative Sentimental

- [긍정적 / 중립적 / 부정적] 비율을 확인한다.

```py
class SentimentalController:
    def __init__(self, session_df, sentimental_dict) -> None:
        self.session_df = session_df
        self.sentimental_dict = sentimental_dict
        self.sentimental_df = self.__make_sentimental_df()

    def calc_total_ratio(self):
        sentimental_df = self.sentimental_df.copy()
        total_sentimental_ratio = (
            sentimental_df[["negative", "positive", "neutral"]].sum(axis=0)
            / sentimental_df[["negative", "positive", "neutral"]]
            .sum(axis=0)
            .sum()
        )
        return total_sentimental_ratio

    def calc_user_ratio(self):
        sentimental_df = self.sentimental_df.copy()
        session_user_ratio_df = self.__calc_session_user_ratio_df()
        user_sentimental_df = session_user_ratio_df.merge(
            sentimental_df.loc[
                :, ["session", "negative", "positive", "neutral"]
            ].drop_duplicates(),
            on=["session"],
        )
        user_sentimental_df.loc[:, ["negative", "positive", "neutral"]] = (
            user_sentimental_df.loc[
                :, ["negative", "positive", "neutral"]
            ].mul(user_sentimental_df["user_ratio"], axis=0)
        )

        user_sentimental_sum = user_sentimental_df.groupby("User")[
            ["negative", "positive", "neutral"]
        ].sum()
        user_ratio_df = user_sentimental_sum.div(
            user_sentimental_sum.sum(axis=1), axis=0
        )
        return user_ratio_df

    def __make_sentimental_df(self):
        sentimental_dict = self.sentimental_dict.copy()
        sentimental_df = pd.DataFrame(sentimental_dict).T
        # preproc
        sentimental_df = sentimental_df.dropna(subset=["document"])
        sentimental_df = sentimental_df["document"].apply(pd.Series)
        sentimental_df = pd.concat(
            [
                sentimental_df.drop(columns=["confidence"]),
                sentimental_df["confidence"].apply(pd.Series),
            ],
            axis=1,
        )
        sentimental_df = sentimental_df.reset_index(names="session")
        return sentimental_df

    def __calc_session_user_ratio_df(self):
        session_df = self.session_df.copy()
        _session_user_cnt_df = (
            session_df.groupby(["session", "User"])
            .size()
            .rename("user_cnt")
            .reset_index()
        )
        _session_cnt_df = (
            session_df.groupby(["session"])
            .size()
            .rename("session_cnt")
            .reset_index()
        )
        session_user_ratio_df = _session_user_cnt_df.merge(
            _session_cnt_df, on="session"
        )
        session_user_ratio_df["user_ratio"] = (
            session_user_ratio_df["user_cnt"]
            / session_user_ratio_df["session_cnt"]
        )

        return session_user_ratio_df

```
