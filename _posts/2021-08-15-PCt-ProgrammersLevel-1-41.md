---
layout: post
title: "[Coding test] Programmers_level 1_약수의 합"
subtitle: "ProgrammersLevel-1-41"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210727_Programmers_level%201_%EC%95%BD%EC%88%98%EC%9D%98%20%ED%95%A9.ipynb)

***

# Programmers_level 1_약수의 합
### 정수 n의 약수를 모두 더한 값을 반환


```python
def solution(n):
    return n + sum([i for i in range(1, (n//2)+1) if n%i == 0])  # n의 반값까지 약수를 리스트 > n + sum > 반환
```


```python
solution(12)
```




    28




```python
solution(5)
```




    6