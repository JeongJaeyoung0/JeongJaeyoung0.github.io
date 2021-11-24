---
layout: post
title: "[Coding test] Programmers_level 2_행렬의 곱셈"
subtitle: "ProgrammersLevel-2-15"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 2차원 행렬 arr1과 arr2를 입력받아, arr1에 arr2를 곱한 결과를 반환

```python
def solution(arr1, arr2):
    # 딱히 설명할 것이 없음
    return [[sum([arr1[w][i] * arr2[i][h] for i in range(len(arr1[0]))]) for h in range(len(arr2[0]))] for w in range(len(arr1))]
```

```python
>>> solution([[1, 4], [3, 2], [4, 1]], [[3, 3], [3, 3]])
[[15, 15], [15, 15], [15, 15]]

>>> solution([[2, 3, 2], [4, 2, 4], [3, 1, 4]], [[5, 4, 3], [2, 4, 1], [3, 1, 1]])
[[22, 22, 11], [36, 28, 18], [29, 20, 14]]

>>> solution([[80, 90, 60], [75, 80, 90], [90, 95, 65], [99, 70, 70]], [[3, 1], [3, 8], [4, 1]])
[[750, 860], [825, 805], [815, 915], [787, 729]]
```