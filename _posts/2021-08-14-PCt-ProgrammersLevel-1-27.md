---
layout: post
title: "[Coding test] Programmers_level 1_행렬의 덧셈"
subtitle: "ProgrammersLevel-1-27"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/90c3b8087e289c317b754ce8ece56a594090e6d8/210712_Programmers_level%201_%ED%96%89%EB%A0%AC%EC%9D%98%20%EB%8D%A7%EC%85%88.ipynb)

***

# Programmers_level 1_행렬의 덧셈
### 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환


```python
def solution(arr1, arr2):    
    return [[x + y for x, y in zip(i, j)] for i, j in zip(arr1, arr2)]
```


```python
solution([[1,2],[2,3]], [[3,4],[5,6]])
```




    [[4, 6], [7, 9]]




```python
solution([[1],[2]], [[3],[4]])
```




    [[4], [6]]