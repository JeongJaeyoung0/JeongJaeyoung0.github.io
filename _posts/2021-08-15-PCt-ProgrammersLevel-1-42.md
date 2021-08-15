---
layout: post
title: "[Coding test] Programmers_level 1_수박수박수박수박수박수?"
subtitle: "ProgrammersLevel-1-42"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210728_Programmers_level%201_%EC%88%98%EB%B0%95%EC%88%98%EB%B0%95%EC%88%98%EB%B0%95%EC%88%98%EB%B0%95%EC%88%98%EB%B0%95%EC%88%98%20.ipynb)

***

# Programmers_level 1_수박수박수박수박수박수?
### 길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 반환


```python
def solution(n):
    return "수박"*(n//2) + "수"*(n%2)   # n//2만큼 "수박"을 반복하고, 뒷 부분에 홀수일 경우 "수"를 붙여서 반환
```


```python
solution(3)
```




    '수박수'




```python
solution(4)
```




    '수박수박'