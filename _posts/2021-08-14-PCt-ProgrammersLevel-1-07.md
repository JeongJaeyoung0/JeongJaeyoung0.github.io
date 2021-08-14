---
layout: post
title: "[Coding test] Programmers_level 1_내적"
subtitle: "ProgrammersLevel-1-7"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/af206dabc43353217edde4f1e15bc6cd87b2a4e5/210621_Programmers_level%201_%EB%82%B4%EC%A0%81.ipynb)

***

# Programmers_level 1_내적
### 길이가 같은 두 배열을 내적하여 출력


```python
def solution(a, b):
    return sum([i*j for i,j in zip(a,b)])       # zip함수로 a, b의 값을 순차로 곱하여 리스트에 저장하고 sum하여 return
```


```python
solution([1,2,3,4], [-3,-1,0,2])
```




    3




```python
solution([-1,0,1], [1,0,-1])
```




    -2