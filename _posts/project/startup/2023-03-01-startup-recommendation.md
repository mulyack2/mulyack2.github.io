---
title: 스타트업-Data_Engineering-Recommendation
date: 2023-03-01
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

## Recommendation

추천시스템을 구축합니다.

- 특징
  - 다양한 ML 모델을 결합하여 사용
    - 모델 Output 통일

## 작업 사항

### 1. 모델 Output 선정

- n명의 개발자가 각자 다른 추천시스템을 구축하였습니다.
  - 이에 이후 다른 추천시스템의 결과물을 병합하여 의사결정을 위해 Output 형식을 미리 통일합니다.

---

### 2. 모델 요구사항

- 추천하는 메뉴가 너무 수렴하지 않도록 한다.
- 다양한 메뉴를 추천할 수 있으며 또한 유저의 취향을 반영한다.

---

### 3. 모델별 특징에 따른 적용 condition 선정

- Content_Based
  - pros : 빠른 속도 보장 , 직접적인 연관성 확인 가능
  - cons : 추천이 단순하여 수렴가능성이 증가, 시계열적인 해석 불가
- Hybrid_Based
  - pros : 추천의 다양성 확보 가능 Cold_Start 문제에 대해서도 어느정도 cover 가능
- DeepLearning_Based
  - pros : 추천의 다양성 확보 가능, 시계열적인 해석 가능
  - cons : Cold_start 문제에 취약
