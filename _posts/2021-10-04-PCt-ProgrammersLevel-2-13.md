---
layout: post
title: "[Coding test] Programmers_level 2_N개의 최소공배수"
subtitle: "ProgrammersLevel-2-13"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : n개의 숫자를 담은 배열 arr이 입력되었을 때 이 수들의 최소공배수를 반환

```python
from fractions import gcd # 최대공약수 라이브러리

def solution(arr):
    answer = 1 # 초기값
    for i in arr: # 배열을 for문
        answer = answer * i / gcd(answer, i) # 최소공배수 = a * b / 최대공약수
    return answer
```

```python
solution([2,6,8,14])
168

solution([1,2,3])
6
```