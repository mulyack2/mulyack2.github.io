---
title: System_Trading-Etc
date: 2023-12-01
categories: [Project, System_Trading]
tags: [Programming, Python, Talk]
---

## System_Trading Series

- [System_Trading-BluePrint](/posts/system_trading-blueprint/)

- [System_Trading-ETL](/posts/system_trading-etl/)

- [System_Trading-Model](/posts/system_trading-model/)

- [System_Trading-Controller](/posts/system_trading-controller/)

---

## ETL

---

### ETL의 분류

- Private의 필요성에 따라
  - api_key와 같은 것이 필요한 소스
  - 그렇지 않은 소스

- Static / Dynamic에 따라
  - api를 통한 수급 형태
  - csv와 같은 고정된 파일 형태

---

### ETL의 convension

[Broker] -> [Extractor] -> [Preproc]

- Broker
  - Broker는 Extractor에서 데이터를 추출 전 준비를 하는 Module
  - 업무
    - Private setting
    - Url / Parameter setting

- Extractor
  - Extractor는 외부와 접촉하여 데이터를 추출하는 Module
  - 업무
    - request / status 확인
    - response -> Data

- Preproc
  - Preproc은 Extractor의 Data를 DB에 저장하기 전 전처리하는 Module
  - 업무
    - 데이터 DB에 넣을 수 있을 정도로 정리

## Model

### Pandas merge_asof

```python
a_df = pd.DataFrame()
b_df = pd.DataFrame()

a_b_df = pd.merge_asof(
            left=a_df, right=b_df,
            by="id", on="date",
            direction="nearest"
)
"""
a_df 와 b_df를 
  - id에 대해서는 반드시 같아야 merge 
  - date에 대해서는 가장 가까운 값으로 merge
    - 시계열을 다루다보면 필요한 방법
"""
```

### Pandas Rolling

rolling을 시계열을 다루다 보면 자주사용하는데

- 이전 값을 기반으로 rolling이 default
- 나는 이번에 앞쪽 값을 기반으로 rolling을 매겨야 해서

```python
backward_rolling = series.rolling(window=n).mean()
front_rolling = series.shift(n).rolling(window=n).mean()
```

> PS  
>
> - 각 데이터 소스별로 3단계 까지 필요하지 않은 곳도 있었고 필요한 곳도 있었습니다.
> - 통일성을 위해 저는 모두 3가지를 구현하였지만, 효율성과 통일성에 대한 고민은 항상 생기는 듯 합니다.

---
