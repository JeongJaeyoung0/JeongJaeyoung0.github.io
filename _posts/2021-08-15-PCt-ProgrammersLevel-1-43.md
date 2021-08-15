---
layout: post
title: "[Coding test] Programmers_level 1_소수 찾기"
subtitle: "ProgrammersLevel-1-43"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210729_Programmers_level%201_%EC%86%8C%EC%88%98%20%EC%B0%BE%EA%B8%B0.ipynb)

***

# Programmers_level 1_소수 찾기
### 1부터 n 사이에 있는 소수의 개수를 반환


```python
def solution(n):
    p=[*range(n+1)]
    for i in p:
        if 1<i:p[i*i::i]=-(i+~n//i)*[0]
        if 1<i:print(i)
    return
```


```python
solution(10)
```


```python
solution(5)
```


```python
n = 10
```


```python
p=[*range(n+1)]
p
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]