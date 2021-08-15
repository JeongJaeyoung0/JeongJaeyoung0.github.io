---
layout: post
title: "[Coding test] Programmers_level 1_제일 작은 수 제거하기"
subtitle: "ProgrammersLevel-1-33"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/cf28883ad5c606788af7ee1b1c649c28c77b98cb/210718_Programmers_level%201_%EC%A0%9C%EC%9D%BC%20%EC%9E%91%EC%9D%80%20%EC%88%98%20%EC%A0%9C%EA%B1%B0%ED%95%98%EA%B8%B0.ipynb)

***

# Programmers_level 1_제일 작은 수 제거하기
### 정수 배열 arr 에서 가장 작은 수를 제거한 배열을 반환. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 반환.


```python
def solution(arr):
    arr.remove(min(arr))    # 리스트에서 최소값 제거
    if len(arr) == 0:       # 제거한 리스트가 빈 리스트일 경우
        return [-1]         # [-1] 반환
    return arr              # 최소값 제거한 리스트 반환
```


```python
solution([4,3,2,1])
```




    [4, 3, 2]




```python
solution([10])
```




    [-1]