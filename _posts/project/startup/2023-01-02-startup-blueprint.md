---
title: 스타트업-Data_Engineering-BluePrint
date: 2023-01-02
categories: [Project, StartUp]
tags: [Programming, Python, Recommendation, Automation]
---

## 스타트업-Data_Engineering-Series

- [스타트업-Data_Engineering-BluePrint](/posts/startup-blueprint/)

- [스타트업-Data_Engineering-DataWareHouse](/posts/startup-datawarehouse/)

- [스타트업-Data_Engineering-Recommendation](/posts/startup-recommendation/)

- [스타트업-Data_Engineering-Automation](/posts/startup-automation/)

- [스타트업-Data_Engineering-Release](/posts/startup-release/)

---

## 서론

- 단체배송 서비스 플랫폼
- 2023.01.02 ~ 2023.06.30

---

## 작업 사항

### 데이터 웨어하우스 구축

- 사내 처음으로 데이터 엔지니어링 팀이 구축되어 데이터 웨어하우스 구축이 필요할 듯
- 백엔드 DB 이해 및 필요 데이터에 대한 의논이 필요하다.

---

### 추천 모델 구축

- 안드로이드 / IOS 앱 내부에서 추천되어야 하기 때문에 속도가 중요할 것 같다.
- 활용 데이터
  - 유저
    - 특성 (성별 / 나이 / 지원금 ...)
    - 로그 (주문 / CTR(Click Through Ratio) ...)
  - 음식
    - 특성 (분류 / 맵기 / 알레르기 ...)

---

### 업무 자동화 시스템 구축

- `배송 가능한` 고객사별 식단을 구축하는 시스템을 만든다.
  - 활용 데이터
    - 식단 데이터
      - 식단이 중복되지 않도록
    - 위치 데이터
      - 고객사 / 음식점 간의 원활한 배송이 가능토록
    - 고객사 / 음식점 클러스터링
      - 단체 배송을 통한 배송 효율이 가능토록

---

### 모델 배포

- `Python ML Model`을 `Java Spring` 서버에서 사용할 수 있도록
