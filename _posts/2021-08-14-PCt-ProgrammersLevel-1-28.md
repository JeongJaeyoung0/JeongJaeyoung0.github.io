---
layout: post
title: "[Coding test] Programmers_level 1_핸드폰 번호 가리기"
subtitle: "ProgrammersLevel-1-28"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/e9fa3807ff36f1e9aad5cb8d654cb869a70d078c/210713_Programmers_level%201_%ED%95%B8%EB%93%9C%ED%8F%B0%20%EB%B2%88%ED%98%B8%20%EA%B0%80%EB%A6%AC%EA%B8%B0.ipynb)

***

# Programmers_level 1_핸드폰 번호 가리기
### 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 반환


```python
def solution(phone_number):
    return '*'*(len(phone_number)-4)+phone_number[-4:]
```


```python
solution("01033334444")
```




    '*******4444'




```python
solution("027778888")
```




    '*****8888'