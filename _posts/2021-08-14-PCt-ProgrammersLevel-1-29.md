---
layout: post
title: "[Coding test] Programmers_level 1_하샤드 수"
subtitle: "ProgrammersLevel-1-29"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/bb0dd430cebe2fb6a788da5cc11adce19fe867a9/210714_Programmers_level%201_%ED%95%98%EC%83%A4%EB%93%9C%20%EC%88%98.ipynb)

***

# Programmers_level 1_하샤드 수
### 자연수 x가 하샤드 수인지 검사하여 반환 (하샤드 수: x의 자릿수의 합으로 x가 나누어지는 수)


```python
def solution(x):
    return x % sum([int(i) for i in str(x)]) == 0
```


```python
solution(10)
```




    True




```python
solution(12)
```




    True




```python
solution(11)
```




    False




```python
solution(13)
```




    False