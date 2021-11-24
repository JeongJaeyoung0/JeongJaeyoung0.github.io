---
layout: post
title: "[Coding test] Programmers_level 1_평균 구하기"
subtitle: "ProgrammersLevel-1-30"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/acb3b0f1e72c96e2339cb873d94b2fc4f4ba2fea/210715_Programmers_level%201_%ED%8F%89%EA%B7%A0%20%EA%B5%AC%ED%95%98%EA%B8%B0.ipynb)

***

# Programmers_level 1_평균 구하기
### 정수 배열 arr의 평균값을 반환


```python
def solution(arr):
    return sum(arr)/len(arr)
```


```python
solution([1,2,3,4])
```




    2.5




```python
solution([5, 5])
```




    5.0