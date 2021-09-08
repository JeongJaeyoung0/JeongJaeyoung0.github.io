---
layout: post
title: "[공모전] 태양광 발전소 입지 선정"
subtitle: "deajeon"
categories: project
tags: project
comments: true
---

![heatMap](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/project/deajeon_heatMap.png?raw=true)
* 개요
    * 공모전명: 2021 빅데이터 분석 및 아이디어 공모전
    * 주최: 대전정보문화산업진흥원
* 상세
    * 주제: 태양광 발전소 입지 선정
    * 기간: 2021.04.30 ~ 2021.06.07
    * 인원: 4명
    * 역할: 팀장
    * 목표: 태양광 발전 효율이 높은 지역 추천
    * 업무: 데이터 확보, 전처리, 발전량 산식 도출, 시각화
    * 환경: Windows, Python(Jupyter), Azure
    * 요약: Python을 이용하여 지난 2년간의 데이터로 대전광역시 동별 태양광 발전 효율 분석 및 상위 25% 지역 선정

* * *

## 개발 개요
**대전 전력자립도 전국 최하위**를 벗어나기 위하여 태양광 사업을 확장되길 바람과, 기존의 효율적이지 못한 태양광 설치를 개선하고자 지역별 발전 효율이 높은 곳을 선정하였다. 또한, 공공시설 건축물의 옥상에 태양광을 설치할 경우 예상되는 발전량과 매출액, 순수익, 투자금 회수기간 등을 도출하여 입지 추천을 하였다.

* 지역별 일 평균 일사량, 온도, 풍속, 풍향, 습도, 미세먼지 엑셀 데이터 저장
* 저장된 데이터를 python으로 불러와 발전량과 데이터의 상관관계 시각화
* 가장 큰 영향을 주는 일사량 기준으로 온도, 풍속을 예측 데이터로 선정
* 데이터양의 부족으로 예측 모델 정확도가 낮아 발전량 산식 및 가중치 적용
* 발전량 산식으로 동별 발전량 상위 추출
* matplotlib으로 차트 작성 및 folium으로 지도 작성
* 공공시설 건축물 옥상에 태양광 설치할 경우 예상 발전량, 순수익 등 산출

## 핵심기술
* 태양광 발전량 상관관계 (태양광 발전량과 관련된 변수 찾기)
    * 발전량은 일사량과 밀접한 관계가 있으며, 예상과 다르게 봄철(3월~6월)의 발전량이 높게 나옴.
    ![analysis](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/project/daejeon_analysis.png?raw=true)
* 발전량 산식
    * 1일 발전량(kWh) = 설비용량 x 일사량 x (1 + 출력온도계수 x (모듈표면온도-25)) / 1000 x 24 x 가중치(0.77)
    * 모듈표면온도    = 온도 + 일사량 x exp(-3.473 - (0.0594 * 풍속))
    * 출력온도계수    = -0.415 / 100

    * *데이터를 수집하여 머신러닝으로 발전량 예측을 하려 하였으나, 데이터의 품질과 양이 부족하여 날씨마루의 기술노트를 참고하였고, 제공받은 데이터와 변수가 맞지 않아 가중치를 적용하여 실제 평균 발전량과 유사한 산식 도출.*

* 태양광 발전량 예측 (일사량, 온도, 풍속에 따른 발전량 예측값 도출)
    * 동일 면적 기준 최상위 동은 최하위 동 대비 136% 발전 가능
    * 상위 25%인 성남동, 문평동, 노은동으로 입지 선정
    ![powerGeneration](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/project/deajeon_powerGeneration.png?raw=true)

* 시각화 (지역별 발전량에 따른 입지 추천)
    * 상위 25%인 3개의 동에 설치 가능 건물(공공건축물) 추천
    ![locationRecommendation](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/project/deajeon_locationRecommendation.PNG?raw=true)

## 결론
* 투자금 회수 기한 약 6.5년 기대
* 에너지 자립률 제고 기대
* 친환경적인 에너지 생태계 구축
* 대전시 예산 절감 효과
* 선정된 건축물 전체에 태양관 발전기를 설치 할 경우 아래 이미지와 같은 순수익 기대
![conclusion](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/project/deajeon_conclusion.png?raw=true)
