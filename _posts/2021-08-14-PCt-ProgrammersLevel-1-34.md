---
layout: post
title: "[Coding test] Programmers_level 1_짝수와 홀수"
subtitle: "ProgrammersLevel-1-34"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/681c2e9af52c0fdc3ac2ada8e6d93f541e38a0b3/210719_Programmers_level%201_%EC%A7%9D%EC%88%98%EC%99%80%20%ED%99%80%EC%88%98.ipynb)

***

# Programmers_level 1_짝수와 홀수
### 정수 num이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환


```python
# if 문
def solution(num):
    return "Even" if num%2 ==0 else "Odd"
```


```python
# 2진수
def solution(num):
    return ["Even", "Odd"][num%2]   # 문자열 리스트에서 짝수면 0번째, 홀수면 1번째 반환
```


```python
solution(3)
```




    'Odd'




```python
solution(4)
```




    'Even'