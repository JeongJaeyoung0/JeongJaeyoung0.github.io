---
layout: post
title: "[Coding test] Programmers_level 1_복서 정렬하기"
subtitle: "ProgrammersLevel-1-56"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 모든 명함을 수납할 수 있는 가장 작은 지갑의 가로*세로를 반환

```python
def solution(sizes):
    # 최소값 초기화
    x = 0
    y = 0
    for i in sizes:
        i.sort()
        # 명함의 가장 긴 부분을 x
        x = max(x, i[1])
        # 명함의 가장 짧은 부분을 y
        y = max(y, i[0])
    return x * y
```

```python
>>> solution([[60, 50], [30, 70], [60, 30], [80, 40]])
4000

>>> solution([[10, 7], [12, 3], [8, 15], [14, 7], [5, 15]])
120

>>> solution([[14, 4], [19, 6], [6, 16], [18, 7], [7, 11]])
133
```