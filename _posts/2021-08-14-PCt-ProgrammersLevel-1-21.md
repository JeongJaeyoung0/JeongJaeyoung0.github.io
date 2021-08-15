---
layout: post
title: "[Coding test] Programmers_level 1_나누어 떨어지는 숫자 배열"
subtitle: "ProgrammersLevel-1-21"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/49d6d77da05922146e8465eddb5c518fcd207710/210705_Programmers_level%201_%EB%82%98%EB%88%84%EC%96%B4%20%EB%96%A8%EC%96%B4%EC%A7%80%EB%8A%94%20%EC%88%AB%EC%9E%90%20%EB%B0%B0%EC%97%B4.ipynb)

***

# Programmers_level 1_나누어 떨어지는 숫자 배열
### array % divisor == 0 인 값을 오름차순으로 정렬한 배열을 반환. 단, 요소가 없을 경우 -1을 담아 반환


```python
def solution(arr, divisor):
    return sorted([i for i in arr if n%divisor==0]) or [-1]   # 앞의 값이 거짓(0) 이면 or 뒤의 값이 반환됨
```


```python
solution([5, 9, 7, 10], 5)
```




    [5, 10]




```python
solution([2, 36, 1, 3], 1)
```




    [1, 2, 3, 36]




```python
solution([3, 2, 6], 10)
```




    [-1]