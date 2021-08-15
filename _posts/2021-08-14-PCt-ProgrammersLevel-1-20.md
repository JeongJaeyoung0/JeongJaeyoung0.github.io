---
layout: post
title: "[Coding test] Programmers_level 1_같은 숫자는 싫어"
subtitle: "ProgrammersLevel-1-20"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/2b582de4ef286bc134c8676db9f2c60325943ecd/210704_Programmers_level%201_%EA%B0%99%EC%9D%80%20%EC%88%AB%EC%9E%90%EB%8A%94%20%EC%8B%AB%EC%96%B4.ipynb)

***

# Programmers_level 1_같은 숫자는 싫어
### 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거. 단, 반환할 때는 원소 순서를 유지.


```python
def solution(arr):
    return [j for i, j in enumerate(arr) if i==0 or arr[i-1]!=j]
```


```python
solution([1,1,3,3,0,1,1])
```




    [1, 3, 0, 1]




```python
solution([4,4,4,3,3])
```




    [4, 3]