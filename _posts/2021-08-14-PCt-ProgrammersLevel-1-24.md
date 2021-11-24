---
layout: post
title: "[Coding test] Programmers_level 1_문자열 내 p와 y의 개수"
subtitle: "ProgrammersLevel-1-24"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210709_Programmers_level%201_%EB%AC%B8%EC%9E%90%EC%97%B4%20%EB%82%B4%20p%EC%99%80%20y%EC%9D%98%20%EA%B0%9C%EC%88%98.ipynb)

***

# Programmers_level 1_문자열 내 p와 y의 개수
### 문자열 s에서 'p'와 'y'의 개수를 비교해 같으면 True, 다르면 False를 반환. 단, 'p', 'y' 모두 하나도 없는 경우는 True를 반환. (대,소문자 구별x)


```python
def solution(s):
    return s.lower().count('p') == s.lower().count('y')
```


```python
solution("pPoooyY")
```




    True




```python
solution("Pyy")
```




    False