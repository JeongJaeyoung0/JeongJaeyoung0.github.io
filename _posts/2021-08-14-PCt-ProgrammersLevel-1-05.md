---
layout: post
title: "[Coding test] Programmers_level 1_로또의 최고 순위와 최저 순위"
subtitle: "ProgrammersLevel-1-5"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/3d151a9ea1ece1fcb35c576dd3bdccc8ff8066e8/210619_Programmers_level%201_%EB%A1%9C%EB%98%90%EC%9D%98%20%EC%B5%9C%EA%B3%A0%20%EC%88%9C%EC%9C%84%EC%99%80%20%EC%B5%9C%EC%A0%80%20%EC%88%9C%EC%9C%84.ipynb)

***

# Programmers_level 1_로또의 최고 순위와 최저 순위
### 2개가 지워진 로또번호를 받고 당첨될수 있는 최대, 최저 등수를 출력


```python
def solution(lottos, win_nums):
    rank=[6,6,5,4,3,2,1]                        # 순위 정의
    zero = lottos.count(0)                      # lottos에 0이 몇개 있는지 카운트
    hit = sum([i in lottos for i in win_nums])  # 맞힌 수 카운트
    return rank[zero+hit],rank[hit]             # 최대: 맞힌수+0개수 / 최소: 맞힌수
```


```python
solution([44, 1, 0, 0, 31, 25], [31, 10, 45, 1, 6, 19])
```




    (3, 5)




```python
solution([0, 0, 0, 0, 0, 0], [38, 19, 20, 40, 15, 25])
```




    (1, 6)
