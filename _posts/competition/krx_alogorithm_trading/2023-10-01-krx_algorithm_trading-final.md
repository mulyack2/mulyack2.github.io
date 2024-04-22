---
title: KRX_alwgorithm_trading-Final
author: mulyack2
date: 2023-10-01
categories: [Competition, KRX_alogorithm_trading]
tags: [Programming, Python]
---

## KRX_Trading-Series

- [KRX_alogorithm_trading BluePrint](/posts/krx_algorithm_trading-blueprint/)

- [KRX_alogorithm_trading Quailifier](/posts/krx_algorithm_trading-qualifier/)

- [KRX_alogorithm_trading Final](/posts/krx_algorithm_trading-final/)

---

## 한국거래소 제 2회 알고리즘 주식투자 경진대회 / 본선

본선

---

## 작업사항

### 1. 한국거래소 유료 데이터 수집

본선에서는 한국거래소에서 제공하는 유료데이터의 수집을 허가해주었다.

#### 1.1 거래원 정보 수집

각 종목별로 날짜별 (개인 / 펀드 / 기관 / 외국인) 등 다양한 거래원의 거래량을 파악 할 수 있다.

#### 1.2 기업의 Fundamental 정보 수집

Dart에서도 제공하지만, 상당히 정제된 수준의 데이터를 수집할 수 있다.

#### 1.3 당연하지만 Ohlcv 정보

---

### 2. Fundamental 기반의 지표 생성

시스템 매매를 진행하면서도 느낀것이지만, 개인적으로 평가하기에

1. Net-Profit / Operation-Profit / PER 와 같은 수익은 기업의 적정가치에 도달하는 속도라고 생각한다.
2. Assets / Equity / PBR 와 같은 자산은 기업의 적정가치(목표치)라고 생각한다.

이 두가지 논리를 기반으로 Model을 구축했다.

---

### 3. Python Library 구현

`Signiture`에 맞게 본선 평가 기간동안 거래할 라이브러리를 구축한다.

- Debug 과정이 한단계 추가될 수록 프로그래밍 피로도가 상당히 커진다.
- whl file로 라이브러리를 구축하고 나의 생각을 보고서로 제출한다.

```plaintext
.
├── __init__.py
├── loader
│   ├── __init__.py
│   ├── api_loader.py
│   └── static_loader.py
├── processor
│   ├── __init__.py
│   ├── model_processor.py
│   ├── order_processor.py
│   └── sector_processor.py
└── trade_func.py

3 directories, 9 files
```

---

![image](/assets/img/_posts/competition/krx_alogorithm_trading/final_model.png)
