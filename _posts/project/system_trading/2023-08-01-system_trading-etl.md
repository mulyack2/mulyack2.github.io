---
title: System_Trading-ETL
date: 2023-08-01
categories: [Project, System_Trading]
tags: [Programming, Python, Data-ETL]
---

## System_Trading Series

- [System_Trading-BluePrint](/posts/system_trading-blueprint/)

- [System_Trading-ETL](/posts/system_trading-etl/)

- [System_Trading-Model](/posts/system_trading-model/)

- [System_Trading-Controller](/posts/system_trading-controller/)

---

## 시스템 매매 ETL

시스템 매매 프로젝트에서 필요한 데이터를 추출합니다.

---

## 시스템 매매에서 필요한 데이터

제가 이번에 진행하는 시스템 매매는 기본적으로 주식매매를 기반으로 합니다.

생각하건데 크게 3가지 분야의 데이터가 필요할 것 같습니다.

1. 기업의 Fundamental을 측정할 데이터
    - 재무제표 데이터
2. 주가 차트에 대한 데이터
    - OHLCV
3. 큰 경제 흐름을 확인할 데이터
    - 국내 / 국외 기준금리
    - 통화량 및 경제상황을 파악할 지표

---

### 기업의 Fundamental을 측정할 데이터

#### [Dart](https://dart.fss.or.kr/) / api_key 필요

- Dart를 활용하는 것이 적절해 보입니다.
- [dart-fss](https://github.com/josw123/dart-fss)와 약간의 detail을 위해 직접 request를 사용하기로 했습니다.

---

### 주가 차트에 대한 데이터

#### [FinanceDataReader](https://github.com/FinanceData/FinanceDataReader)

- 저에게 가장 매력적인 라이브러리는 FinanceDataReader 였습니다.
- 속도도 좋고, 데이터도 상당히 정확합니다.

#### [pykrx](https://github.com/sharebook-kr/pykrx)

- 거래원을 분석할 수 있는 정보를 제공합니다.
- 무분별한 호출시 일시 block을 당하는 듯합니다.

---

### 큰 경제 흐름을 확인할 데이터

#### [Ecos](https://ecos.bok.or.kr/) / api_key 필요

- 한국은행에서 제 수준에서 필요한 모든 경제지표를 제공합니다.
- [PublicDataReader](https://github.com/WooilJeong/PublicDataReader)와 함께 추출하면 될것 같습니다.

#### [Fred](https://fred.stlouisfed.org/) / api_key 필요

- 미국의 경제지표는 Fred(Federal Reserve Economic Data)에서 추출 합니다.
- [fredpy](https://github.com/letsgoexploring/fredpy)를 활용합니다.

## 여담

다양한 데이터 소스를 살펴 보았습니다.

![image](/assets/img/_posts/project/system_trading/data-source-checking.png)
