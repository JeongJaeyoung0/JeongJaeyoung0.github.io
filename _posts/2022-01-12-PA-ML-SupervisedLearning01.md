---
layout: post
title: "[AI] ML - 머신러닝 개념"
subtitle: "SupervisedLearning01"
categories: python
tags: ai
comments: true
---

# 머신러닝의 개념
- 데이터 기반으로 패턴을 학습하고 결과를 예측하는 알고리즘 기법
 
* * *

# 머신러닝 분류
- 지도학습
    - 분류(Classifier): 예측하고자 하는 타겟값이 범주형 변수(이진분류, 다중분류)
        - 결정트리 분류(DecisionTreeClassifier)
            - Graphviz 패키지: 결정 트리 시각화 (https://www.graphviz.org 에서 상세 자료)
            - export_graphviz(): 사이킷런에서 Graphviz 패키지와 쉽게 인터페이스 할 수 있도록 API 제공
        - 랜덤포레스트 분류(RandomForestClassifier)
        - 그래디언 부스팅 분류(GradientBoostingClassifier)
        - 가우시안NB 분류(GaussianNaiveBayesClassifier)
        - SVC(SupportVectorMachines)
    - 회귀(Regressor): 예측하고자 하는 타겟값이 실수인 경우(연속성)
        - 선형 회귀 (Linear regression)
            - 변수들이 선형적으로 연결되어 있는 경우
            - 특이치에 영향을 받기 쉬우므로 빅데이터 집합 분석에는 부적합
        - 로지스틱 회귀 (LogisticRegression)
            - 종속 변수에 이산 값이 있는 경우(0 or 1, True or False)
            - 대상 변수에서 거의 동일한 값이 발생하는 대규모 데이터 세트에 효과
            - 변수들의 순위를 지정할 때 문제를 일으킬 수 있기 때문에 상관성이 높은 독립 변수들이 데이터 집합에 포함되면 안됨
        - 리지 회귀 (RidgeRegression)
            - 독립 변수들 사이에 높은 상관 관계가 있는 경우
            - 정규화, 규제화
            - 모델 복잡성을 줄이는데 사용
        - 라쏘 회귀 (LassoRegression)
            - 모델 복잡성을 줄여주는 정규화 기법
            - 필요한 요소들만 사용하고 나머지를 0으로 설정함으로써 과대적합을 방지
        - 다항 회귀 (PolynomialRegression)
            - 선형 모델을 사용하여 비선형 데이터 집합을 모델링
        - 랜덤포레스트 회귀(RandomForestRegressor)
            - 앙상블 기법
        - 그라디언트 부스팅 회귀(GradientBoostingRegressor)
            - 앙상블 기법
    - 추천 시스템
    - 시각/음성 감지/인지
    - 텍스트 분석, NLP
- 비지도학습
    - 군집화(Clustering)
    - 차원축소(DimensionReduction)
- 강화학습

* * *

# 파이썬 머신러닝 주요 패키지
- 머신러닝 패키지: 사이킷럿(Sklearn) 등
- 딥러닝 패키지: 텐서플로우(TensorFlow), 케라스(Keras) 등
- 행렬, 선형대수, 통계 패키지: 넘파이(Numpy), 사이파이(SciPy) 등
- 데이터 핸들링: 판다스(Pandas) 등
- 시각화: 맵플롯립(Matplotlib) 등
