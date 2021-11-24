---
layout: post
title: "[Coding test] Programmers_level 1_폰켓몬"
subtitle: "ProgrammersLevel-1-9"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/e411a81f81234f9aa96ec1047a5d9b51a1bbc3bf/210623_Programmers_level%201_%ED%8F%B0%EC%BC%93%EB%AA%AC.ipynb)

***

# Programmers_level 1_폰켓몬
### 종류가 중복될 수 있는 n개의 배열중 2/n개를 선택 할 수 있는 경우, 가장 많은 종류를 가질 수 있는 값을 출력


```python
def solution(nums):
    return min(len(nums)//2, len(set(nums)))    # 가질 수 있는 개수, 종류의 개수 중 작은 수
```


```python
solution([3,1,2,3])
```




    2




```python
solution([3,3,3,2,2,4])
```




    3




```python
solution([3,3,3,2,2,2])
```




    2