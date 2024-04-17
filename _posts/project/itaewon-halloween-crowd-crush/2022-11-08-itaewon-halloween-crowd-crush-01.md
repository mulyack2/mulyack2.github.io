---
title: 이태원-압사-사고-BluePrint-[01]
date: 2022-11-08
categories: [Project, 이태원-압사-사고]
tags: [Programming, Python, Data-Analysis, Data-Visualze]
---

# 이태원-압사-사고 Series
- [이태원-압사-사고 BluePrint[01]](https://mulyack2.github.io/posts/itaewon-halloween-crowd-crush-01/)   

- [이태원-압사-사고 ETL[02]](https://mulyack2.github.io/posts/itaewon-halloween-crowd-crush-02/)   

- [이태원-압사-사고 Visualize[03]](https://mulyack2.github.io/posts/itaewon-halloween-crowd-crush-03/)   

- [이태원-압사-사고 Prediction[04]](https://mulyack2.github.io/posts/itaewon-halloween-crowd-crush-04/)   

---

# 서론
이태원 압사 사고로 많은 생명을 잃었습니다.  
이 사건을 감정적 / 정치적인 견해는 제외하고 데이터를 통해 살펴보고 싶어졌습니다.

---

## 프로젝트 개요
공공 데이터 / 서울시 오픈 데이터를 바탕으로 인구의 밀집에 대한 적절한 조사를 진행하려고 합니다.  
적절한 인사이트를 도출 할 수 있다면, 이러한 사건이 일어나는 condition을 파악하고 이후 `재발 방지 대책`을 구축할 수 있을 것 입니다.  

---

## 프로젝트에 알고 싶은 것
1. `한번도 일어나지 않은 일을 예측하는 것`은 가능한가?
    - 통계학적인 사고 방식으로는 불가능해 보이는듯한 이 문제에 대한 결과를 도출 하고 싶습니다.

2. `데이터로 볼 때 사고가 일어날 만한 이상치`에 있는 상황이었나?
    - 이번 사건이 인구 밀집의 지표로 이상치에 있는 상황이 었는지 확인하고 싶습니다.

---

## 프로젝트 활용 데이터
1. `서울교통공사 지하철 일별 / 역별 / 시간대별 승하차 인원`
2. `소상공인시장진흥공단 상가(상권)정보`
3. `서울특별시 행정동별 서울생활인구`

3가지를 메인 데이터로 상황을 살펴볼 예정입니다.