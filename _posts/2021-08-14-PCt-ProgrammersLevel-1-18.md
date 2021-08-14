---
layout: post
title: "[Coding test] Programmers_level 1_2016년"
subtitle: "ProgrammersLevel-1-18"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/f3644ef6b0ff77aee311026cc61f1b984afb71ef/210702_Programmers_level%201_2016%EB%85%84.ipynb)

***

# Programmers_level 1_2016년
### 2016년 1월 1일은 금요일이다. 2016년 a월 b일은 무슨 요일인지 영문 대문자로 출력


```python
import datetime
def solution(a, b):
    days = ['MON','TUE','WED','THU','FRI','SAT','SUN']
    return days[datetime.date(2016, a, b).weekday()]
```


```python
solution(5, 24)
```




    'TUE'