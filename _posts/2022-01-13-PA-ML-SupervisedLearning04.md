---
layout: post
title: "[AI] ML - 머신러닝 성능 평가"
subtitle: "SupervisedLearning04"
categories: python
tags: ai
comments: true
---
# 머신러닝 성능 평가

### 지도학습 - 분류

- 정확도(Accuracy)
    - 정확도 = 예측 정답 건수 / 전체 예측 건수
    - ML 모델 성능 왜곡 가능성이 있기 때문에, 정확도 수치만으로 평가할 수 없음 (불균형한 레이블 값일 경우)
- 오차행렬(Confusion Matrix)
    - 이진 분류 성능 지표로 많이 사용
    - 사이킷런에서 confusion_matrix() API 제공
    <table
        border="1">
        <thead>
            <tr align="center">
                <td></td>
                <th>Negative(0)</th>
                <th>Positive(1)</th>
            </tr>
        </thead>
        <tbody>
            <tr align="center">
                <th>Negative(0)</th>
                <td>TN<br>(True Negative)</td>
                <td>FP<br>(False Positive)</td>
            </tr>
            <tr align="center">
                <th>Positive(1)</th>
                <td>FN<br>(False Negative)</td>
                <td>TP<br>(True Positive)</td>
            </tr>
        </tbody>
    </table>
    - 정확도 = (TN + TP) / (TN + FP + FN + TP)

- 정밀도(Precision)
    - TP / (FP + TP)
    - 정밀도가 중요 지표인 경우는 실제 Nagative 음성 데이터를 Positive로 잘못 판단하게 되면 업무상 큰 영향이 발생하는 경우 (스팸 메일)
- 재현율(Recall)
    - TP / (FN + TP)
    - 재현율이 중요 지표인 경우는 실제 Positive 양성 데이터를 Negative로 잘못 판단하게 되면 업무상 큰 영향이 발생하는 경우 (암 판단 모델)
    > 정밀도, 재현율 모두 높은 수치를 얻는 것이 좋다. 둘 중 한 지표만 매우 높고 다른 수치는 매우 낮은 결좌를 나타내는 경우는 바람직하지 않다.<br>
    > 업무 특성에 따라 임계값을 조정해 특정 수치를 높일 수 있지만, 한쪽을 높이면 다른 수치가 낮아지는 트레이드오프 관계이다.
- F1 Score
    - 정밀도와 재현율을 결합한 지표
    - 정밀도와 재현율이 어느 한쪽으로 치우치지 않는 수치를 나타낼 때 상대적으로 높은 값을 가짐
    - 2 * (정밀도 * 재현율) / (정밀도 + 재현율)
    - 사이킷런에서 f1_score() API 제공
- ROC AUC
    - ML 이진 분류 모델의 성능 판단하는 중요한 지표
    - FPR(False Positive Rate)이 변할 때 TPR(True Positive Rate)이 어떻게 변하는지 나타내는 곡선
    - FPR = FP / (FP + TN) = 1 - TNR = 1 - 특이성
    - 1에 가까울 수록 좋은 수치

<br>

### 지도학습 - 회귀

- MAE (Mean Absolute Error)
    - $$MAE = \frac{1}{n} \displaystyle\sum_{i=1}^{n} |Yi- \hat{Y}i|$
    - 실제 값과 예측 값의 차이를 절댓값으로 변환해 평균
- MSE (Mean Squared Log Error)
    - $$MSE = \frac{1}{n} \displaystyle\sum_{i=1}^{n} (Yi- \hat{Y}i)^2$$
    - 실제 값과 예측값의 차이를 제곱해 평균
- RMSE (Root Mean Squared Eerror)
    - $$RMSE = \sqrt{\frac{1}{n} \displaystyle\sum_{i=1}^{n} (Yi- \hat{Y}i)^2}$$
    - MSE에 루트를 씌운 값
- R2 Score(Coefficient of Determination, 결정계수)
    - $$R^2 = \frac{예측값 Variance}{실제값 Variance}$$
    - 분산 기반으로 예측 성능을 평가하며, 1에 가까울수록 정확도가 높음
