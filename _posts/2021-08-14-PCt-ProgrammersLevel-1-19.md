---
layout: post
title: "[Coding test] Programmers_level 1_가운데 글자 가져오기"
subtitle: "ProgrammersLevel-1-19"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/1d9bd87d105041ac27c69dd618483b160bb1da91/210703_Programmers_level%201_%EA%B0%80%EC%9A%B4%EB%8D%B0%20%EA%B8%80%EC%9E%90%20%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0.ipynb)

***

# Programmers_level 1_가운데 글자 가져오기
### 단어 s의 가운데 글자를 반환. 단, 짝수면 가운데 두글자를 반환.


```python
import math
def solution(s):
    mid = math.ceil(len(s)/2-1)     # 중앙값
    if len(s)%2: answer = s[mid]    # 길이가 짝수일 경우
    else: answer = s[mid:mid+2]     # 길이가 홀수일 경우
    return answer
```


```python
solution("abcde")
```




    'c'




```python
solution("qwer")
```




    'we'