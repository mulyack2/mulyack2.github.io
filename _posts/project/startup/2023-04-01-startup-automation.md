---
title: 스타트업-Data_Engineering-Automation
date: 2023-04-01
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

## Automation

업무자동화 시스템을 구축합니다.
고객사의 식단과 음식점의 업무를 최적화합니다.

- 특징
  - 다양한 source 기반의 model 구축 / score 기반의 병합
    - 거리 기반 모델
    - 선호도 기반 모델
    - 중복도 기반 모델

## 작업 사항

---

### 1. 거리 기반 모델

1. 고객사 / 음식점 클러스터링을 통한 단체배송 그룹 구축
2. API 기반의 배송 거리 최적화 진행
3. 거리기반의 cluster 및 배송 가능 조합별 score 계산

---

### 2. 선호도 기반 모델

1. 각 고객사 별 주요 주문 제품 확인
2. 각 고객사 별 주요 고객 특징 (성별 / 나이)
3. 각 고객사 별 요구사항 확인 (샐러드 필수 / 탕류 필수)
4. 각 고객사 별 음식점에 대한 score 계산

---

### 3. 중복도 기반 모델

1. 음식점이 제공 가능한 음식 다양성에 따른 과거중복도 penalty 계산
2. 음식점이 일일 가능량에 따른 일일중복도 penalty 계산
