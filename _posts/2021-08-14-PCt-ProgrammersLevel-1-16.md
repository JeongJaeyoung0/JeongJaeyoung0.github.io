---
layout: post
title: "[Coding test] Programmers_level 1_약수의 개수와 덧셈"
subtitle: "ProgrammersLevel-1-16"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/8765645b02368a9f09a31097225a46b8a2d6763a/210630_Programmers_level%201_%EC%95%BD%EC%88%98%EC%9D%98%20%EA%B0%9C%EC%88%98%EC%99%80%20%EB%8D%A7%EC%85%88.ipynb)

***

# Programmers_level 1_약수의 개수와 덧셈
### left부터 right까지 모든 정수들 중 약수의 개수가 짝수는 더하고, 홀수는 뺀 수를 출력


```python
def solution(left, right):
    return sum([i if len([j for j in range(1,i+1) if i%j==0])%2 == 0 else -i for i in range(left, right+1) ])
```


```python
solution(13, 17)
```




    43




```python
solution(24, 27)
```




    52