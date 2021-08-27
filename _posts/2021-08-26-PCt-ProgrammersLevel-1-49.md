---
layout: post
title: "[Coding test] Programmers_level 1_부족한 금액 계산하기"
subtitle: "ProgrammersLevel-1-49"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/a52f325deb4193437451525eac661dbe23878e1e/210826_Programmers_level%201_%20%E1%84%87%E1%85%AE%E1%84%8C%E1%85%A9%E1%86%A8%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%80%E1%85%B3%E1%86%B7%E1%84%8B%E1%85%A2%E1%86%A8%20%E1%84%80%E1%85%A8%E1%84%89%E1%85%A1%E1%86%AB%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5.ipynb)

***

# programmers_level 1_부족한 금액 계산하기
### 이용료: price, n번쨰 이용료: n*price, count번 타게 되면 money에서 얼마가 모자라는지를 반환 (단, 금액이 부족하지 않으면 0을 반환)


```python
def solution(price, money, count):
    answer = sum([price*(i+1) for i in range(count)]) - money   # 부족금액: 1~count번 까지 price를 곱하고 money를 뺀값
    if answer < 0:  # 부족금액이 0보다 작을 경우(부족하지 않는 경우)
        answer = 0  # 0을 반환
    return answer
```


```python
solution(3, 20, 4)
```




    10
