---
title: MongoDB를 살펴보자
date: 2024-05-01
categories: [Pracetice, Bigdata]
tags: [Looking, Bigdata, MongoDB]
---

## 서론

`IBM Data-Science Course`를 마치고 `IBM Data-Engineer Course`를 진행하고 있습니다.

`MongoDB`를 공부하며 상당히 매력적인 부분이 많은 것 같아서 조금 남겨두려고 합니다.

## NoSQL

NoSQL의 4대 분류

- Key - Values
  - ex) redis
- Document
  - ex) MongoDB
- Columns
  - ex) Cassandra
- Graph
  - ex)

## MongoDB

`MongoDB`는 Document based DB입니다.

> 주요 특징  
> 제가 이해한 바로는 `json`을 저장할 수 있다.  
> -> 즉 유연한 스키마 구성이 가능하다.

### Structure

|MySQL|MongoDB|
|---|---|
|Database|Database|
|Table|Collection|

요런 느낌입니다.

### Utils

`Python`으로 다루기 편하게 pymongo가 있습니다.  
특히 코드가 좀 객체지향스타일인데, 이 때문에 `python`에서 사용과 실제 `sql`이 상당히 유사합니다.

```plaintext
# In MongoDB

## select db
use campusManageMentDB

## mycollection 데이터 전부 추출
db.students.find()
```

---

```python
# In Python
from pymongo import MongoClient

uri = "mongodb://USER:PASSWORD@uri/test"
## Engine
client = MongoClient(uri)
## Db
campusDB = client.campusManageMentDB
## Collection
students = campustDB.students

## mycollection 데이터 전부 추출
students.find()
```

## 결론

혹시 진행하게 될 수 있는 프로젝트 하나가 상당히 `MongoDB`를 사용하기 좋은 프로젝트가 될 것 같습니다.  
진행하게 된다면, `MongoDB`를 활용하여 json 데이터를 적절하게 수집 / 저장 해야겠습니다.
