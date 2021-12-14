---
layout: post
title: "[AI] ML - 지도 학습 (Supervised Learning)"
subtitle: "SupervisedLearning"
categories: python
tags: ai
comments: true
---

# 머신러닝 종류
  - 분류 (Classifier)
    - 이진분류 (Binary Classification)
      - 0 or 1을 분류
    - 다중분류 (Multi-class Classification)
      - 다중 클래스 분류
  - 회귀 (Regressor)
    - 선형 회귀 (Linear regression)
      - 변수들이 선형적으로 연결되어 있는 경우
      - 특이치에 영향을 받기 쉬우므로 빅데이터 집합 분석에는 부적합
    - 로지스틱 회귀 (Logistic regression)
      - 종속 변수에 이산 값이 있는 경우(0 or 1, True or False)
      - 대상 변수에서 거의 동일한 갓ㅂ이 발생하는 대규모 데이터 세트에 효과
      - 변수들의 순위를 지정할 떄 문제를 일으킬 수 있기 떄문에 상관성이 높은 독립 변수들이 데이터 집합에 포함되면 안됨
    - 리지 회귀 (Ridge regression)
      - 독립 변수들 사이에 높은 상관 관계가 있는 경우
      - 정규화, 규제화
      - 모델 복잡성을 줄이는데 사용
    - 라쏘 회귀 (Lasso regression)
      - 모델 복잡성을 줄여주는 정규화 기법
      - 필요한 요소들만 사용하고 나머지를 0으로 설정함으로써 과대적합을 방지
    - 다항 회귀 (Polynomial regression)
      - 선형 모델을 사용하여 비선형 데이터 집합을 모델링

# 분류의 성능 평가 지표
  - Accuracy
  - Recall
  - Precision
  - F1 score
  
  https://hleecaster.com/ml-accuracy-recall-precision-f1/

# 회귀의 성능 평가 지표
  - MAE (Mean Absolute Error)
  - MSE (Mean Squared Log Error)
  - RMSE (Root Mean Squared Eerror)
  - RMSLE(Root Mean Square Logarithmic Error)
  - R2 Score(Coefficient of Determination, 결정계수)


  https://rk1993.tistory.com/entry/%EB%AA%A8%EB%8D%B8-%EC%84%B1%EB%8A%A5-%ED%8F%89%EA%B0%80-%EC%A7%80%ED%91%9C-%ED%9A%8C%EA%B7%80-%EB%AA%A8%EB%8D%B8-%EB%B6%84%EB%A5%98-%EB%AA%A8%EB%8D%B8
