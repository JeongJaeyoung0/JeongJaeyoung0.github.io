---
layout: post
title: "[Coding test] Programmers_level 2_최댓값과 최솟값"
subtitle: "ProgrammersLevel-2-17"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 문자열 s에는 공백으로 구분된 숫자들중 "(최소값) (최대값)"형태의 문자열을 반환

```python
def solution(s):
    # 공백을 기준으로 split하여, 각각 int로 변환 후 오름차순 정렬
    n = sorted(map(int, s.split(' ')))
    # 최소값(0번째) 최대값(-1번째)를 문자열로 반환
    return "%s %s" % (n[0], n[-1])
```

```python
>>> solution("1 2 3 4")
"1 4"

>>> solution("-1 -2 -3 -4")
"-4 -1"

>>> solution("-1 -1")
"-1 -1"
```