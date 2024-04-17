---
title: 이태원-압사-사고-Etc-[99]
date: 2022-11-23
categories: [Project, 이태원-압사-사고]
tags: [Programming, Python, Data-Analysis, Data-Visualze]
---

## 이태원-압사-사고 Series

- [이태원-압사-사고 BluePrint[01]](/posts/itaewon-halloween-crowd-crush-01/)

- [이태원-압사-사고 ETL[02]](/posts/itaewon-halloween-crowd-crush-02/)

- [이태원-압사-사고 Visualize[03]](/posts/itaewon-halloween-crowd-crush-03/)

- [이태원-압사-사고 Prediction[04]](/posts/itaewon-halloween-crowd-crush-04/)  

---

## 프로젝트 하며 배운것

### CustomDict

key가 없는 값을 넣으면 key를 제공하는 dictionary

```python
class CustomDict(dict):
    def __missing__(self,key):
        return key

custom_dict = CustomDict()
```

---

### Clustering Paramter Tunning

상권 clustering을 하는 과정에서 다양한 clustering을 진행하고 파라미터를 조절 했습니다.
제 데이터의 경우는 적절하게 cluster가 되지 못한 데이터를 두는것이 중요했습니다.
이에 DBscan을 좀 공부하고, 파라미터를 tunning 하는 경험을 했습니다.

```python
from sklearn.cluster import DBSCAN

eps = 0.005
min_samples = 50

dbscan = DBSCAN(eps=eps, min_samples=min_samples)
```

---
