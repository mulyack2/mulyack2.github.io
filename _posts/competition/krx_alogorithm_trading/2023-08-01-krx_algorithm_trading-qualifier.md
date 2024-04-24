---
title: KRX_algorithm_trading-Qualifier
author: mulyack2
date: 2023-08-01
categories: [Competition, KRX_alogorithm_trading]
tags: [_All, Finance]
---

## KRX_Trading-Series

- [KRX_alogorithm_trading BluePrint](/posts/krx_algorithm_trading-blueprint/)

- [KRX_alogorithm_trading Quailifier](/posts/krx_algorithm_trading-qualifier/)

- [KRX_alogorithm_trading Final](/posts/krx_algorithm_trading-final/)

---

## 한국거래소 제 2회 알고리즘 주식투자 경진대회 / 예선

예선

---

## 작업사항

### 1. 시계열 데이터의 chunk

```python
def get_x_y_dataset(arraylist, CFG):
    i_window = CFG["input_window"]
    o_window = CFG["output_window"]

    x_dataset = list()
    y_dataset = list()

    for idx in range(len(arraylist) - i_window - o_window + 1):
        _x = arraylist[idx : idx + i_window]
        _y = arraylist[idx + i_window : idx + i_window + o_window]
        x_dataset.append(_x)
        y_dataset.append(_y)

    x_dataset = np.array(x_dataset)
    y_dataset = np.array(y_dataset)
    return x_dataset, y_dataset
```

### 2. 유사도 기반의 Model

```python
def get_cosine_similarity(array_1, array_2):
    cosine_similarity = np.dot(array_1, array_2) / (
        np.linalg.norm(array_1) * np.linalg.norm(array_2)
    )
    return cosine_similarity

def get_similarity_df(x_dataset, y_dataset, final_x):
    similarity_results = list()
    for x_data, y_data in zip(x_dataset, y_dataset):
        _similarity_score = get_cosine_similarity(x_data, final_x)
        similarity_results.append(
            {
                "similarity_score": _similarity_score,
                "actual_y": y_data,
            }
        )
    similarity_df = pd.DataFrame(similarity_results)
    return similarity_df


def get_similarity_main_df(x_dataset, y_dataset, final_x, n):
    similarity_results = list()
    for x_data, y_data in zip(x_dataset, y_dataset):
        _similarity_score = get_cosine_similarity(x_data, final_x)
        similarity_results.append(
            {
                "similarity_score": _similarity_score,
                "actual_y": y_data,
            }
        )
    similarity_df = pd.DataFrame(similarity_results)
    similarity_main_df = similarity_df.nlargest(n, "similarity_score")
    return similarity_main_df

def get_pred_y(similarity_df):
    pred_y = (similarity_df["similarity_score"] * similarity_df["actual_y"]).mean()
    return pred_y

```
