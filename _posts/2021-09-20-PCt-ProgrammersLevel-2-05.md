---
layout: post
title: "[Coding test] Programmers_level 2_타겟 넘버"
subtitle: "ProgrammersLevel-2-05"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : n개의 음이 아닌 정수를 더하거나 빼서 타겟 넘버를 만들수 있는 경우의 수를 반환

```python
# 재귀 풀이
def solution(numbers, target):
    if numbers == []:
        if target == 0:
            return 1
        else:
            return 0
    else:
        return solution(numbers[1:], target+numbers[0]) + solution(numbers[1:], target-numbers[0])
```


```python
# product 풀이
from itertools import product
def solution(numbers, target):
    l = [(x, -x) for x in numbers]
    s = list(map(sum, product(*l)))
    return s.count(target)
```

```python
>>> solution([1, 1, 1, 1, 1], 3)
5
```