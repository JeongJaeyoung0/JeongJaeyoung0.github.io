---
layout: post
title: "[Coding test] Programmers_level 1_x만큼 간격이 있는 n개의 숫자"
subtitle: "ProgrammersLevel-1-26"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/a5275f449a37039c997a2cd2c51ad43b2d7d2cc9/210711_Programmers_level%201_x%EB%A7%8C%ED%81%BC%20%EA%B0%84%EA%B2%A9%EC%9D%B4%20%EC%9E%88%EB%8A%94%20n%EA%B0%9C%EC%9D%98%20%EC%88%AB%EC%9E%90.ipynb)

***

# Programmers_level 1_x만큼 간격이 있는 n개의 숫자

### 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 반환


```python
# for문 풀이
def solution(x, n):
    return [x*i for i in range(1, n+1)]
```


```python
# range 풀이
def solution(x, n):
    return list(range(x, x*(n+1), x))
```


```python
solution(2, 5)
```




    [2, 4, 6, 8, 10]




```python
solution(4, 3)
```




    [4, 8, 12]




```python
solution(-4, 2)
```




    [-4, -8]