---
layout: post
title: "[Coding test] Programmers_level 1_정수 내림차순으로 배치하기"
subtitle: "ProgrammersLevel-1-36"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/c9ae1397adadc11d4a96bad21ed4c383a3e70fca/210721_Programmers_level%201_%EC%A0%95%EC%88%98%20%EB%82%B4%EB%A6%BC%EC%B0%A8%EC%88%9C%EC%9C%BC%EB%A1%9C%20%EB%B0%B0%EC%B9%98%ED%95%98%EA%B8%B0.ipynb)

***

# Programmers_level 1_정수 내림차순으로 배치하기
### 정수 n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 반환


```python
def solution(n):
    return int(''.join(sorted(list(str(n)), reverse=True))) # 문자열 > 리스트 > 내림차순 정렬 > join > 정수열 > 반환
```


```python
solution(118372)
```




    873211