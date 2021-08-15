---
layout: post
title: "[Coding test] Programmers_level 1_자연수 뒤집어 배열로 만들기"
subtitle: "ProgrammersLevel-1-37"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/cf7bbefadea8e297fc1bc493018e5ba4b78e6d0d/210722_Programmers_level%201_%EC%9E%90%EC%97%B0%EC%88%98%20%EB%92%A4%EC%A7%91%EC%96%B4%20%EB%B0%B0%EC%97%B4%EB%A1%9C%20%EB%A7%8C%EB%93%A4%EA%B8%B0.ipynb)

***

# Programmers_level 1_자연수 뒤집어 배열로 만들기
### 자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 반환


```python
# for문
def solution(n):
    return [int(i) for i in str(n)[::-1]]   # 문자열 > for문 > 정수열 > 리스트 > 반환
```


```python
# reversed
def solution(n):
    return list(map(int, reversed(str(n)))) # 문자열 > 리버스 > map 정수열 > 리스트 > 반환
```


```python
solution(12345)
```




    [5, 4, 3, 2, 1]