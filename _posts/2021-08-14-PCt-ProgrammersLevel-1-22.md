---
layout: post
title: "[Coding test] Programmers_level 1_두 정수 사이의 합"
subtitle: "ProgrammersLevel-1-22"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/c4bbd2fc33927238b431e05e752aa9e8b474b1c3/210706_Programmers_level%201_%EB%91%90%20%EC%A0%95%EC%88%98%20%EC%82%AC%EC%9D%B4%EC%9D%98%20%ED%95%A9.ipynb)

***

# Programmers_level 1_두 정수 사이의 합
### a와 b사이의 모든 정수의 합을 반환


```python
# for문 풀이
def solution(a, b):
    num = sorted([a, b])                            # a, b 오름차순 정렬
    return sum([i for i in range(num[0],num[1]+1)]) #a부터 b까지 모든 수 sum
```


```python
# 등차수열 풀이
def solution(a, b):
    return (abs(a-b)+1)*(a+b)//2                    # S = n(a+b)/2
```


```python
solution(3, 5)
```




    12




```python
solution(3, 3)
```




    3




```python
solution(5, 3)
```




    12