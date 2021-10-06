---
layout: post
title: "[Coding test] Programmers_level 2_최솟값 만들기"
subtitle: "ProgrammersLevel-2-16"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 배열 A, B가 주어질 때 A, B에서 각각 한 개의 숫자를 뽑아 곱한 수의 총 합이 최솟값을 반환

```python
def solution(A,B):
    # 최소값일 경우는 한개의 배열은 오름차순, 다른 한개의 배열은 내림차순으로 정렬 후 각각 곱한 수
    return sum(a * b for a, b in zip(sorted(A), sorted(B, reverse = True)))
```

```python
>>> solution([1, 4, 2], [5, 4, 4])
29

>>> solution([1, 2], [3, 4])
10
```