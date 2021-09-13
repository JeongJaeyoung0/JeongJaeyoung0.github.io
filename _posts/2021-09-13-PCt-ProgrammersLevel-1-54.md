---
layout: post
title: "[Coding test] Programmers_level 1_없는 숫자 더하기"
subtitle: "ProgrammersLevel-1-54"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 0~9중 없는 숫자들의 합을 리턴

```python
def solution(numbers):
    return sum([i for i in range(10) if not i in numbers])
```

```python
>>> solution([1,2,3,4,6,7,8,0])
14

>>> solution([5,8,4,0,6,7,9])
6
``` 