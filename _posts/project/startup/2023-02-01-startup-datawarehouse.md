---
title: 스타트업-Data_Engineering-DataWareHouse
date: 2023-02-01
categories: [Project, StartUp]
tags: [_All, Recommendation, Automation]
---

## 스타트업-Data_Engineering-Series

- [스타트업-Data_Engineering-BluePrint](/posts/startup-blueprint/)

- [스타트업-Data_Engineering-DataWareHouse](/posts/startup-datawarehouse/)

- [스타트업-Data_Engineering-Recommendation](/posts/startup-recommendation/)

- [스타트업-Data_Engineering-Automation](/posts/startup-automation/)

- [스타트업-Data_Engineering-Release](/posts/startup-release/)

---

## DataWareHouse

데이터 웨어하우스를 구축합니다.

- 특징
  - DB : MySQL
  - Pipeline : Airflow
  - Platform : GCP(Google Cloud Platform)

## 작업 사항

### 1. DB 이해 및 Data_WareHouse setting

처음으로 상용 백엔드 DB를 만져보니 정말 복잡했습니다.

백엔드 팀과 회의를 하며 DB를 이해하는 시간을 가졌습니다.

백엔드 DB는 `Normalization`으로 인해 데이터 엔지니어링에 적합하지 않은 형식을 가졌습니다.

이에 바로 ML 모델에 사용할 수 있는 형식으로 데이터를 `Denormalization` 진행했습니다.

---

### 2. Data_Pipeline 구축 / Airflow

- Airflow를 처음 다루어보았습니다.

- Python + ipynb의 가장 쉬운 조합으로 프로그래밍을 시작해서 그런지 조금 어려웠습니다.

- Dag는 추출 시간 기반으로 나누었습니다.
  - 오전 / 오후 추출 데이터
    - 아침 배송 / 점심 배송 결과
  - 일간 추출 데이터
    - 일간 배송량 / 소비량 결과
    - 일간 고객 주문 결과
  - 주간 추출 데이터
    - 주간 고객 결제량
  - 격주 추출 데이터
    - 고객사 예정 식단

---

### 3. Data_WareHouse 배포

상용에서 활용하다 보니, 보안 관련 작업을 해야할 것이 좀 있었습니다.

- 접속 가능 IP 제한
- DB 유저별 권한 제한
