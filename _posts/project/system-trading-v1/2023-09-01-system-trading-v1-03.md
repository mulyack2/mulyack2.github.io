---
title: System-Trading-v1-Model-[03]
date: 2023-09-01
categories: [Project, System-Trading]
tags: [Programming, Python, Modeling]
---

## 시스템 매매 Modeling

시스템 매매 프로젝트에서 의사결정을 진행할 모델을 구축한다.

---

## Model의 종류

### 1. 현재 상황이 투자를 할 상황인지 선택하는 Model

`model - macro`

- Macro하게 매력적이지 않은 시점에 투자를 할 이유는 없다고 생각합니다.
- 이번 프로젝트는 국내 주식 시스템 매매를 기반합니다.
  - 국내 주식 시장이 현 시점에서 매력이 있는지 없는지를 평가하는 Model이 필요합니다.

#### 금리 기반의 평가

- 미국금리와 한국금리의 비교는 상황평가에 꽤나 유용해 보입니다.
  - 한국금리 > 미국금리 일때 KOSPI가 상승하는 모습을 보여주었습니다.

![image](/assets/img/_posts/project/system-trading-v1/model_1_bir.png)

- Model
  - 미국금리와 한국금리의 n_window 간의 합산을 통해 현재 한국금리의 점수를 평가합니다.
  - 0.5 이상의 값이 나온다면, 현재 한국금리가 우위에 있음을 나타냅니다.
  - 금리 golden-cross 기반보다는 적절한 격차를 두는 것이 좋아보였습니다.

#### 통화량 기반의 평가

- 통화량이 증가한다면 KOSPI는 결국 상승하는 모습을 보여주었습니다.
  - 다만 하락보다 상승에 더 큰 연관을 보이는 듯 합니다.

![image](/assets/img/_posts/project/system-trading-v1/model_1_m1.png)

- Model
  - 통화량의 기울기를 통해 현재 상황을 파악합니다.
    - 통화량의 기울기가 n_window 중 .5 이상이라면 꽤나 높은 수준으로 통화량이 증가함을 알 수 있습니다.

### 2. 투자할 종목을 선정하는 Model

`model - Fundamental`

- 1차적인 Filtering을 할 수 있는 Model이 필요합니다.
- 저는 1차적인 Filtering을 Fundamental 요인을 기반으로 진행하기로 하였습니다.

#### Raw Fundamental 기반의 평가

종목의 가격에 독립적으로 재무제표의 상태를 평가하는 모델입니다.

- 재무제표의 지표들의 기울기와 값을 파악하여 기업의 건전성을 확인합니다.

```plaintext
- [당기순이익, 유동자본]의 n년 간 기울기.
- 가장 최근의 영업이익.
- 업종내에서 자본대비 이익 비율이 어떠한가.
```

#### Price Fundamental 기반의평가

종목의 가격에 종속적으로 재무제표의 상태를 평가하는 모델입니다.

- 재무제표의 지표대비 종목가격을 파악하여 기업의 평가수준을 확인합니다.

```plaintext
- 업종의 평균 PBR / PER는 어떠한가
- 종목의 평균 PBR
```

### 3. 투자할 종목 중 `현재` 매수가 적절한 종목을 선택하는 Model

`model - Technical`

- Fundamental로 투자할만한 종목을 추린 후, 차트를 기반으로 현재 가격에 대한 분석을 진행합니다.
- Technical Analysis를 그리 선호 하지는 않습니다만, 한다면 RSI 지표를 사용합니다.
- 이번 프로젝트에서는 `Position Analysis`라는 Model을 구축하여 의사결정에 활용합니다.

#### Position Anaysis

일단 맥락은 이런 느낌입니다.
![position_analysis](/assets/img/_posts/project/system-trading-v1/position_analysis.png)

- 우리가 차트에서 가격(시가,종가,저가,고가)과 거래량을 통해 최근 주식 구매자들의 평단가를 예측하는 것입니다.

1. 차트에서 가격과 거래량 정보를 추출
2. 가격과 거래량을 통해 평단가 sample 추출
3. 평단가 sample을 기반으로 최다 밀도 가격을 추출
4. 이를 통해 현재 가격의 평단가 순위를 파악

가장 저렴하게 사는 것이 좋다고 생각할 수 있지만, 저는 하위 20 ~ 60 프로 사이 정도로 구매하는 것이 좋다고 생각합니다.
