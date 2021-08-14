---
layout: post
title: "[Coding test] Programmers_level 1_두 개 뽑아서 더하기"
subtitle: "ProgrammersLevel-1-17"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/c16695c5ff103a8d3a061ebc3c1886c86f8c9547/210701_Programmers_level%201_%EB%91%90%20%EA%B0%9C%20%EB%BD%91%EC%95%84%EC%84%9C%20%EB%8D%94%ED%95%98%EA%B8%B0.ipynb)

***

# Programmers_level 1_두 개 뽑아서 더하기
### 정수 배열이 주어질 때, 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 오름차순으로 출력


```python
def solution(numbers):
    return sorted({numbers[i]+numbers[j] for i in range(len(numbers)-1) for j in range(i+1, len(numbers))})
```


```python
solution([2,1,3,4,1])
```




    [2, 3, 4, 5, 6, 7]




```python
solution([5,0,2,7])
```




    [2, 5, 7, 9, 12]