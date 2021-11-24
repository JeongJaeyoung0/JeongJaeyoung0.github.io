---
layout: post
title: "[Coding test] Programmers_level 1_문자열 다루기 기본"
subtitle: "ProgrammersLevel-1-44"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/30a106298e0c4c67d17af704313921bf9e658805/210822_Programmers_level%201_%E1%84%86%E1%85%AE%E1%86%AB%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%A7%E1%86%AF%20%E1%84%83%E1%85%A1%E1%84%85%E1%85%AE%E1%84%80%E1%85%B5%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB.ipynb)

***

# programmers_level 1_문자열 다루기 기본
### 문자열 길이가 4 혹은 6이고, 숫자로만 구성돼있는지 확인해주는 함수


```python
def solution(s):
    return s.isdigit() and len(s) in (4, 6)
```


```python
solution("a234")
```




    False




```python
solution("1234")
```





    True
