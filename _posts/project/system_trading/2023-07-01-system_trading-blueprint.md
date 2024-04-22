---
title: System_Trading-BluePrint
date: 2023-07-01
categories: [Project, System_Trading]
tags: [Programming, Python]
---

## System_Trading Series

- [System_Trading-BluePrint](/posts/system_trading-blueprint/)

- [System_Trading-ETL](/posts/system_trading-etl/)

- [System_Trading-Model](/posts/system_trading-model/)

- [System_Trading-Controller](/posts/system_trading-controller/)

---

## 시스템 매매 프로젝트

시스템 매매 프로젝트를 진행합니다.

---

## 시스템 매매를 위해 필요한 것

매매의 cycle

[구매]

1. 시장종목 중 구매할 종목을 선정한다.

2. 구매할 종목들의 구매 비율을 선정한다.

3. 구매한다.

[판매]

1. 보유종목 중 판매할 종목을 선정한다.

2. 판매할 종목들의 판매 비율을 선정한다.

3. 판매한다.

---

### Model

- [구매_1] 구매할 종목을 선정하는 Model
- [구매_2] 구매할 종목들의 구매 비율을 선정하는 Model

- [판매_1] 판매할 종목을 선정하는 Model
- [판매_2] 판매할 종목들의 판매 비율을 선정하는 Model

---

### Data

- [구매할 종목을 선정하는 Model]을 위한 Data
- [판매할 종목을 선정하는 Model]을 위한 Data

---

### Controller

- [구매 / 판매를 위한 Controller]

---

### Visualizer

- [구매한 종목에 대한 Visualizer]
- [경제 지표에 대한 Visualizer]
