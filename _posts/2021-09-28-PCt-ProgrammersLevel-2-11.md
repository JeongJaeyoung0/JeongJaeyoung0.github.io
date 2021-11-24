---
layout: post
title: "[Coding test] Programmers_level 2_피보나치 수"
subtitle: "ProgrammersLevel-2-11"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : n번째 피보나치 수를 1234567로 나눈 나머지를 반환

```python
def solution(n):
    fib = [0, 1] # 피보나치 수 0, 1번째 생성
    for i in range(n - 1): # 미리 2개를 생성해 두었기 때문에 2개 적게 for문
        fib.append(fib[i] + fib[i + 1]) # 피보나치 수 추가
    return fib[n] % 1234567 # n번째 피보나치 수를 1234567로 나눈 나머지를 반환
```

```python
>>> solution(3)
2

>>> solution(5)
5
```
