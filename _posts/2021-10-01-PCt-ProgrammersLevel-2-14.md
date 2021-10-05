---
layout: post
title: "[Coding test] Programmers_level 2_JadenCase 문자열 만들기"
subtitle: "ProgrammersLevel-2-14"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열이다. 문자열 s가 주어 졌을 때 JadenCase로 바꾼 문자열을 반환

```python
def solution(s):
    # ' '로 split후 ''일 경우는 else로 그렇지 않을 경우 첫 번째 문자는 대문자, 그 뒤 문자는 소문자로 치환하고 join후 반환)
    return ' '.join(map(lambda a: a[0].upper() + a[1:].lower() if a else a, s.split(' ')))
```

```python
>>> solution("3people unFollowed me")
"3people Unfollowed Me"

>>> solution("for the last week")
"For The Last Week"
```