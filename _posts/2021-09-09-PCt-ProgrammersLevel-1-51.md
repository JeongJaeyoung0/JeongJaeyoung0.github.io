---
layout: post
title: "[Coding test] Programmers_level 1_숫자 문자열과 영단어"
subtitle: "ProgrammersLevel-1-50"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 일부 자리수를 영단어로 바꾼 카드를 원래 숫자로 리턴

```python
def solution(s):
    # 숫자를 순서대로 영단어로 리스트
    en = ["zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"]
    # 영단어를 for문 통해 e로, for문 순서에 따라서 0~9를 i
    for i, e in enumerate(en):
        # e(영단어)를 i(숫자)로 치환
        s = s.replace(str(e),str(i))
    # 정수로 리턴
    return int(s)
```

```python
>>> solution("one4seveneight")
1478
>>> solution("23four5six7")
234567
>>> solution("2three45sixseven")
234567
>>> solution("123")
123
```