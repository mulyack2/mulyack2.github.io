---
title: Airflow를 다루다 발생하는 흔한 오류들
date: 2024-05-04
categories: [Practice, Bigdata, Airflow]
tags: [Practice, Bigdata, Airflow]
---

## Airflow Errors

저는 `Airflow`를 접한 이후로 대체로 파이프라인을 에어플로우로 구축합니다.  
발생했던 오류인데, 종종 `왜 안되지?!` 하는 경우들이 있어 생각 할 거리를 적어둡니다.

## Is Json Serializable

`Airflow`에서는 데이터를 넘겨주는 작업이 많이 일어납니다.  
`Task`간의 데이터를 넘겨줄 때 그 데이터는 `Json Serializable`해야 합니다.  

```python
# 이런건 안된다!
@task
def return_dataframe():
    return pd.DataFrame()

@task
def format_dataframe(df):
    return df.reset_index()

df = return_dataframe()
processed_df = format_dataframe(df)

# 이런건 된다!
@task
def return_dataframe_json():
    return pd.DataFrame().to_json()

@task
def format_dataframe(df_json):
    df = pd.json_normalize(df_json)
    return df.reset_index()

df_json = return_dataframe_json()
processed_df = format_dataframe(df_json)
```
