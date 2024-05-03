---
title: NoSQL을 살펴보자
date: 2024-05-01
categories: [Pracetice, BigData]
tags: [Looking, Bigdata, NoSQL]
---

## 서론

`NoSQL`을 살펴보죠.

> `NoSQL` <-> `RDBMS`  
> 제가 이해한 바로는 / 한줄요약 하자면  
> 관계형 데이터베이스가 아니면, NoSQL 입니다.

## NoSQL

### 특징

- 비관계적이다.(Not Relational)
- 반정형 / 비정형 데이터를 쉽게 저장 가능하다.
- 분산 환경에서 잘 작동한다.
  - 고가용성과 내결함성을 지닌다.

### 종류

기본적으로 크게 4종류를 생각할 수 있습니다.  
최근에는 LLM의 출연으로 `Vector DB`가 추가되는 분위기 입니다.

![image](/assets/img/_posts/practice/nosql/nosql_types.png)

### RDBMS vs NoSQL

- RDBMS
  - ACID
    - Atomic
    - Consistent
    - Isolated
    - Durable
- NoSQL [Availability / Scalable / Resilience]
  - BASE
    - Basically Available
    - Soft state
    - Eventually consistent

### 분산 데이터베이스

NoSQL은 주로 분산 데이터베이스 구축에 Native 한 것 같습니다.  
분산 데이터 베이스의 특징은

- 데이터를 두 사이트 이상에 중복저장 함으로 재해복구에 강한 것 같습니다

## Etc

NoSQL 시스템은 사실상 RDBMS를 대체하지 않습니다.

- 금융거래와 같이 `RDBMS`가 필수적인 부분이 분명히 있습니다.
