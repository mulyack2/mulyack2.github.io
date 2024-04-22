---
title: KRX_algorithm_trading-BluePrint
author: mulyack2
date: 2023-07-01
categories: [Competition, KRX_alogorithm_trading]
tags: [Programming, Python]
---

## KRX_Trading-Series

- [KRX_alogorithm_trading BluePrint](/posts/krx_algorithm_trading-blueprint/)

- [KRX_alogorithm_trading Quailifier](/posts/krx_algorithm_trading-qualifier/)

- [KRX_alogorithm_trading Final](/posts/krx_algorithm_trading-final/)

---

## 한국거래소 제 2회 알고리즘 주식투자 경진대회

시스템 트레이딩 프로젝트 진행중 겸사겸사 대회가 있어 진행했다.

---

## 작업사항

최근 마무리한 추천시스템을 기반으로 예선에 참가한다.

차트의 유사도를 통해 이후에 차트가 나아갈 방향을 예측하는 방식의 모델을 구현하였다.

### 1. 예선

theme : `자본시장 데이터 및 공공 데이터를 활용하여 Long-Short 포트폴리오 구성`

1. 데이터를 기반으로 종목별 Long / Short / None 선택

- Idea : 유사도
  - 유사도를 기반으로 현재 Macro한 시장의 지표들을 통해 현재와 유사한 과거 시대를 파악
  - 유사도를 기반으로 과거 시대 차트와 현재 차트의 유사도를 비교
    - 상승률이 높은 차트와 유사도가 높은 종목 : Long
    - 상승률이 낮은 차트와 유사도가 높은 종목 : Short

---

### 2. 본선

theme : `자본시장 데이터 및 공공 데이터를 활용하여 가상투자를 진행하는 알고리즘 제작`

1. Signiture에 맞는 파이썬 라이브러리 구축
2. 라이브러리에 대한 보고서 작성

- Idea : 지표 기울기
  - 각 기업의 재무제표를 바탕으로 적절한 지표를 생성한다.
    - 지표들의 기울기를 바탕으로 적정 주가를 파악한다.

---
