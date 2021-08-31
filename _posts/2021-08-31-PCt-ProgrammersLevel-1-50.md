---
layout: post
title: "[Coding test] Programmers_level 1_상호 평가"
subtitle: "ProgrammersLevel-1-50"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/cb8c8f78e1049a9f853436e15a3b0fa6b99b0db7/210831_Programmers_level%201_%E1%84%89%E1%85%A1%E1%86%BC%E1%84%92%E1%85%A9%20%E1%84%91%E1%85%A7%E1%86%BC%E1%84%80%E1%85%A1.ipynb)

***

# programmers_level 1_상호 평가
### 상호평가 점수중 자신의 점수가 율일한 최대, 최소일 경우 제외하여 평균값을 산출하고, 점수에 따른 학점을 반환


```python
def solution(scores):
    import numpy as np
    num = range(len(scores))
    # 각 학생의 점수들끼리 리스트
    sco = [[scores[j][i] for j in num] for i in num]
    # 자기 자신의 평가 점수가 최소값 or 최대값일 경우 제거
    for i in num:
        # 각 점수 리스트의 최소값 인덱스
        minIndex = [n for n, s in enumerate(sco[i]) if s == min(sco[i])]
        # 각 점수 리스트의 최대값 인덱스
        maxIndex = [n for n, s in enumerate(sco[i]) if s == max(sco[i])]
        # 자기 자신의 점수가 유일한 최소값일 경우 삭제
        if len(minIndex) == 1 and i in minIndex:
            del sco[i][i]
            continue
        # 자기 자신의 점수가 유일한 최대값일 경우 삭제
        if len(maxIndex) == 1 and i in maxIndex:
            del sco[i][i]
            continue
    # 각 점수 리스트별 평균값
    meanSco = [np.mean(sco[i]) for i in num]
    # 90이상 A, 80이상 B, 70이상 C, 50이상 D, 50미만 F을 조인하여 반환
    return ''.join(["A" if i >= 90 else "B" if i >= 80 else "C" if i >= 70 else "D" if i >= 50 else "F" for i in meanSco])
```


```python
solution([[100,90,98,88,65],[50,45,99,85,77],[47,88,95,80,67],[61,57,100,80,65],[24,90,94,75,65]])
```




    FBABD



```python
solution([[50,90],[50,87]])
```




    DA



```python
solution([[70,49,90],[68,50,38],[73,31,100]])
```




    CFD
