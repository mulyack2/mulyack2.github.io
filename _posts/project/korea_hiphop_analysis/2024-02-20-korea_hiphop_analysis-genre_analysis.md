---
title: 한국힙합_쇠퇴-장르변화
date: 2024-02-20
categories: [Project, 한국힙합_쇠퇴]
tags: [Programming, Python, Data-Analysis, Data-Visualze]
---

## 한국힙합_쇠퇴 Series

- [한국힙합_쇠퇴 BluePrint](/posts/korea_hiphop_analysis-blueprint/)

- [한국힙합_쇠퇴 음악_이용자_실태조사](/posts/korea_hiphop_analysis-market_analysis/)

- [한국힙합_쇠퇴 장르변화](/posts/korea_hiphop_analysis-genre_analysis/)

---

## 국내힙합의 장르변화

__장르가 Experimental화 되어 갈때 그 장르는 쇠퇴한다?__ 라는 인상적인 내용의 영상이 있었습니다.

이를 바탕으로 국내힙합의 Experimental화 또한 살펴봅니다.

![image](/assets/img/_posts/project/korea_hiphop_analysis/experimental.png)

---

## 작업 사항

---

### 1. 음악장르 분석기 구축

먼저 음악 데이터에서 장르를 추출할 모델을 구축합니다.

1. [FMA(Free Music Archive)](https://github.com/mdeff/fma) 데이터셋 활용
2. [librosa (Python Music Analysis OpenSource)](https://github.com/librosa/librosa) 활용
3. 2019 ~ 2023 한국힙합어워즈 음악분석

결론적으로 장르 분석기를 학습시킨 결과

- Multinomial Classification(5 labels) : 77% 정확도
![image](/assets/img/_posts/project/korea_hiphop_analysis/multi_class.png)

- Binary Classification (Hiphop / Not-Hiphop) : 85% 정확도
![image](/assets/img/_posts/project/korea_hiphop_analysis/binary_class.png)

정도의 성능을 보였습니다.

---

### 2. 음악 clustering을 통한 장르 유사도 측정

![image](/assets/img/_posts/project/korea_hiphop_analysis/music_similiarity.png)

---

### 3. 국내 힙합에 대한 모델 적용

#### 1. 시계열에 따른 국내 힙합 장르분석기 결과

- 국내힙합 multi-label 분석기 분석결과
![image](/assets/img/_posts/project/korea_hiphop_analysis/multi_class_kh.png)

- 국내힙합 binary-label 분석기 분석결과
![image](/assets/img/_posts/project/korea_hiphop_analysis/binary_class_kh.png)

#### 2. 시계열에 따른 국내 힙합 장르 변화

![image](/assets/img/_posts/project/korea_hiphop_analysis/genre_diff_kh.png)

## 고찰

- 실제로 Experimental 부분의 장르가 좀 많이 올라왔다.
  - 어쩌면 이게 쇠퇴하는 힙합을 부흥시키려는 시도일 수도 있지만, 결론은 그렇다.
-
