---
title: 스타트업-Data_Engineering-Release
date: 2023-05-01
categories: [Project, StartUp]
tags: [Programming, Python, Automation]
---

## 스타트업-Data_Engineering-Series

- [스타트업-Data_Engineering-BluePrint](/posts/startup-blueprint/)

- [스타트업-Data_Engineering-DataWareHouse](/posts/startup-datawarehouse/)

- [스타트업-Data_Engineering-Recommendation](/posts/startup-recommendation/)

- [스타트업-Data_Engineering-Automation](/posts/startup-automation/)

- [스타트업-Data_Engineering-Release](/posts/startup-release/)

---

## Release

프로젝트를 배포합니다.

- 특징
  - `Python-Django`를 통한 배포
    - 추천시스템에 대한 배포
    - 업무자동화 시스템에 대한 배포
  - `ML-BackOffice` 구축
    - ML parameter 설정 / 대쉬보드 구축

## 작업 사항

---

### 1. GCP setting

#### 1. Django Server Setting

Django Sever를 실행할 수 있게 한다.

#### 2. Airflow Data_Pipeline Setting

Airflow Sever를 실행할 수 있게 한다.

#### 3. Django DB(MySQL Setting)

Django DB 와 DataWareHouse DB를 배포한다.

---

### 2. Django Server

#### 1. Django ML Release

`추천시스템`과 `업무자동화 시스템`을 실행할 수 있는 백오피스를 구축한다.

#### 2. Django ML DashBoard

`추천시스템`과 `업무자동화 시스템`의 파라미터를 조절하고 결과를 확인하는 백오피스를 구축한다

---

### 3. Docker

Django server를 Dockerfile을 통해 이미지화 하고 배포한다.
