---
title: KakaoTalk-OpenChat_Analysis-BluePrint
date: 2024-03-01
categories: [Project, OpenChat_Analysis]
tags: [_All, NLP]
---

## KakaoTalk-OpenChat_Analysis Series

- [KakaoTalk-OpenChat_Analysis-BluePrint](/posts/open_chat_analysis-blueprint/)
- [KakaoTalk-OpenChat_Analysis-eda_statistics](/posts/open_chat_analysis-eda_statistics/)
- [KakaoTalk-OpenChat_Analysis-ml](/posts/open_chat_analysis-ml/)
- [KakaoTalk-OpenChat_Analysis-DL](/posts/open_chat_analysis-dl/)

---

## 서론

카카오톡 오픈채팅을 기반으로 파악하는 인간관계.

## 작업사항

### 1. 채팅 EDA

채팅 데이터의 간단한 EDA 및 데이터 전처리

- START_DATE
- END_DATE
- TOTAL_USER
- TOTAL_TALK

### 2. 채팅 통계 분석 (Statistic Analysis)

채팅 데이터의 통계적 해석

- Long Talker
- Short Talker
- Talk Ratio
- Talk Length Ratio

### 3. 채팅 관계 분석 (ML Analysis)

채팅 데이터의 ML 기반의 해석(관계분석)

- 채팅의 session화
- session을 통한 관계 분석

### 4. 채팅 감성 분석 (DL Analysis)

채팅 데이터의 DL 기반의 해석(감성분석)

- 채팅방에 대한 감성분석
- 유저에 대한 감성분석
  - Noramlized 감성
  - Absolute 감성
