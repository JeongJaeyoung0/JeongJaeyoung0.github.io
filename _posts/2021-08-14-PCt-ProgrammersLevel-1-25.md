---
layout: post
title: "[Coding test] Programmers_level 1_직사각형 별찍"
subtitle: "ProgrammersLevel-1-25"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/17208120edcb5ce9a98b469094731e947892b188/210710_Programmers_level%201_%EC%A7%81%EC%82%AC%EA%B0%81%ED%98%95%20%EB%B3%84%EC%B0%8D%EA%B8%B0.ipynb)

***

# Programmers_level 1_직사각형 별찍기
### 정수 n과 m이 주어질 때, '*'을 가로(n) x 세로(m) 직사각형 형태를 출력


```python
n, m = map(int, input().strip().split(' '))
print((n*'*'+'\n')*m)
```

    5 3
    *****
    *****
    *****