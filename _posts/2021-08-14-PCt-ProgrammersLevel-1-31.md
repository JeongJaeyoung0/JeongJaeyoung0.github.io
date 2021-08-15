---
layout: post
title: "[Coding test] Programmers_level 1_콜라츠 추측"
subtitle: "ProgrammersLevel-1-31"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b4d12c670a8cf0d5b7867c89afc169918bafde62/210716_Programmers_level%201_%EC%BD%9C%EB%9D%BC%EC%B8%A0%20%EC%B6%94%EC%B8%A1.ipynb  )

***

# Programmers_level 1_콜라츠 추측
### 콜라츠 추측을 몇 번 반복해야 하는지 반환. 단, 500번을 반복해도 1이 되지 않으면 -1을 반환.
##### 콜라츠 추측
##### 1. 입력된 수가 짝수일 경우 2로, 홀수일 경우 3을 곱하고 1을 더함
##### 2. 1의 결과가 1이 될 때까지 반복


```python
def solution(num):
    answer = 0
    while num != 1:
        answer += 1
        num = num/2 if num%2 == 0 else num*3+1
        if answer == 501:
            return -1
    return answer
```


```python
solution(6)
```




    8




```python
solution(16)
```




    4




```python
solution(626331)
```




    -1