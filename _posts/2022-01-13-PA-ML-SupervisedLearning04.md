---
layout: post
title: "[AI] ML - 머신러닝 성능 평가"
subtitle: "SupervisedLearning04"
categories: python
tags: ai
comments: true
---
# 머신러닝 성능 평가

### 지도학습
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
            <td>TN</td>
            <td>FP</td>
        </tr>
        <tr align="center">
            <th>Positive(1)</th>
            <td>FN</td>
            <td>TP</td>
        </tr>
    </tbody>
</table>

- 정밀도(Precision)
- 재현율(Recall)
- F1 Score
- ROC AUC