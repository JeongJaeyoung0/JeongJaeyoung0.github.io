---
layout: post
title: "[Coding test] Programmers_level 2_짝지어 제거하기"
subtitle: "ProgrammersLevel-2-08"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 같은 알벳이 붙어있을 경우 제거하고, 모두 제거 될 경우 1을, 아닐 경우 0을 반환

```python
def solution(s):
    l = [] # 제거되지 않는 문자 담을 리스트
    for i in s: # 문자 하나씩 for문
        if len(l) > 0 and l[-1] == i: # 리스트가 0 초과이면서, 현재 문자가 마지막 문자와 같을 경우
            l.pop() # 리스트의 마지막 문자 삭제
        else: # 마지막 문자와 다를 경우
            l.append(i) # 현재 문자 리스트에 추가
    return int(len(l) == 0) # 리스트 길이가 0일 경우는 True로 1, 아닐 경우 False로 0을 반환
```

```python
>>> solution('baabaa')
1
>>> solution('cdcd')
0
```