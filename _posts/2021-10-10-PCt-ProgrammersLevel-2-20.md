---
layout: post
title: "[Coding test] Programmers_level 2_올바른 괄호"
subtitle: "ProgrammersLevel-2-20"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : '(' 또는 ')' 로만 이루어진 문자열 s가 주어졌을 때, 문자열 s가 올바른 괄호이면 True, 그렇지 않으면 False을 반환

```python
def solution(s):
    # 기준 값
    x = 1
    # 문자열 하나씩 반복문
    for a in s:
        # x가 0일 경우 False
        if x == 0:
            return False
        # "("일 경우 x+1, ")"일 경우 x-1 / 시작부터 ")"일 경우 x가 0이 되기 때문에 False이 됨
        x = x+1 if a == "(" else x-1
    # 반복문이 다 돌고도 x가 1일 경우 True
    return x == 1
```

```python
>>> solution("()()")
True
>>> solution("(())()")
True
>>> solution(")()(")
False
>>> solution("(()(")
False
```