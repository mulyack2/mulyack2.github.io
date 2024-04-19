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

- Macro하게 매력적이지 않은 시점에 투자를 할 이유는 없다고 생각합니다.
- 이번 프로젝트는 국내 주식 시스템 매매를 기반합니다.
  - 국내 주식 시장이 현 시점에서 매력이 있는지 없는지를 평가하는 Model이 필요합니다.

### 2. 투자할 종목을 선정하는 Model

- 1차적인 Filtering을 할 수 있는 Model이 필요합니다.
- 저는 1차적인 Filtering을 Fundamental 요인을 기반으로 진행하기로 하였습니다.

### 3. 투자할 종목 중 `현재` 매수가 적절한 종목을 선택하는 Model

- Fundamental로 투자할만한 종목을 추린 후, 차트를 기반으로 현재 가격에 대한 분석을 진행합니다.
- Technical Analysis를 그리 선호 하지는 않습니다만, 한다면 RSI 지표를 사용합니다.
- 이번 프로젝트에서는 `Position Analysis`라는 Model을 구축하여 의사결정에 활용합니다.
