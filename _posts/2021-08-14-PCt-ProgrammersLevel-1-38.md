---
layout: post
title: "[Coding test] Programmers_level 1_자릿수 더하기"
subtitle: "ProgrammersLevel-1-38"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/ee329ce2837043b58155d0fc7ecc6acee288a6fd/210723_Programmers_level%201_%EC%9E%90%EB%A6%BF%EC%88%98%20%EB%8D%94%ED%95%98%EA%B8%B0.ipynb)

***

# Programmers_level 1_자릿수 더하기
### 자연수 n에서 각 자릿수의 합을 구하여 반환


```python
def solution(n):
    return eval('+'.join(list(str(n)))) # 문자열 > 리스트 > join > 문자열 그대로 eval로 연산 > 반환
```


```python
solution(123)
```




    6




```python
solution(987)
```




    24