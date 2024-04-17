---
title: 이태원-압사-사고-ETL-[02]
date: 2022-11-09
categories: [Project, 이태원-압사-사고]
tags: [Programming, Python, Data-ETL, Data-Preprocessing]
---

# 이태원-압사-사고 Series
- [이태원-압사-사고 BluePrint[01]](/posts/itaewon-halloween-crowd-crush-01/)   

- [이태원-압사-사고 ETL[02]](/posts/itaewon-halloween-crowd-crush-02/)   

- [이태원-압사-사고 Visualize[03]](/posts/itaewon-halloween-crowd-crush-03/)   

- [이태원-압사-사고 Prediction[04]](/posts/itaewon-halloween-crowd-crush-04/)  

---
## 프로젝트 활용 데이터
1. `서울교통공사 지하철 일별 / 역별 / 시간대별 승하차 인원`  
[data-source](https://data.seoul.go.kr/dataList/OA-12921/F/1/datasetView.do#)

2. `소상공인시장진흥공단 상가(상권)정보`  
[data-source](https://www.data.go.kr/tcs/dss/selectFileDataDetailView.do?publicDataPk=15083033)

3. `서울특별시 행정동별 서울생활인구`  
[data-source](https://www.data.go.kr/data/15083607/fileData.do)

---

## 1. 서울교통공사 지하철 일별 / 역별 / 시간대별 승하차 인원

#### 특이사항 :  연도별로 xlsx와 csv가 혼재되어 있다.
```
['./../data/raw/metro/서울교통공사 2017년 일별 역별 시간대별 승하차인원(1_8호선).xlsx',
 './../data/raw/metro/서울교통공사 2020년 일별 역별 시간대별 승하차인원(1_8호선).csv',
 './../data/raw/metro/서울교통공사 2021년 일별 역별 시간대별 승하차인원(1_8호선).csv',
 './../data/raw/metro/서울교통공사 2018년 일별 역별 시간대별 승하차인원(1_8호선).xlsx',
 './../data/raw/metro/서울교통공사 2019년 일별 역별 시간대별 승하차인원(1_8호선).xlsx',
 './../data/raw/metro/서울교통공사_역별 일별 시간대별 승하차인원 정보_20221231.csv']
```

- 본능적으로 연도별로 column이 다를 것이 느껴진다.
    - 특별히 어려운 일은 아니지만 손이 가는 작업.
    - 실수하지 않도록 모두 같은 column임을 확인하는 함수를 사용 했다.

```python
def is_column_rdy(df, columns):
    if all(df.columns == columns):
        return True
    else:
        return False    
    
if is_column_rdy(metro_2017, columns):
    metro_2017.to_csv("./../data/preproc/metro/metro_2017.csv")
else:
    print("Column Not Rdy")
```

---

## 2. 소상공인시장진흥공단 상가(상권)정보
- 별일 없이 column이 좀 많은 csv

```
상권업종대분류명
    {'관광/여가/오락', '부동산', '생활서비스', '소매', '숙박', '스포츠', '음식', '학문/교육'}
-> '음식' 부분만 사용하기로 한다.
```


---

## 3. 서울특별시 행정동별 서울생활인구
- 별문제 없지만 데이터가 조금 큰 편이라 분리가 필요했다.

- filter를 쓰면 기분이 좋다.
```python
population_2022_dir_paths = list(
    filter(lambda x: "2022" in x, population_dir_paths)
)
```

---

# 참고
- 1차 전처리
    - data-lake 에서 data-warehouse로 가져오는 느낌이다.
    - 프로젝트에서 데이터를 활용할 수 있게 데이터를 준비한다.
- 2차 전처리
    - 데이터를 [모델 / 시각화]에 사용할 수 있게 처리하는 느낌이다.