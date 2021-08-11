---
layout: post
title: "[Coding test] Baekjoon_level 10_재귀-2"
subtitle: "BaekjoonLevel10-2"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/7a4893fa45be7c8da3ed0d23c4d6597c683cd1a0/210607_Baekjoon_coding%20test_level%2010_%EC%9E%AC%EA%B7%80-1.ipynb)

***

2021.06.08
# coding test_Baekjoon_level 10_재귀-2


```python
# 11729 (히노이 탑 이동 순서)-1
def h(a,b,c):
    if a==1:
        return [[b,c]]
    return h(a-1,b,6-b-c)+[[b,c]]+h(a-1,6-b-c,c)
a=int(input())
p=h(a,1,3)
print(2**a-1)
for i in range(len(p)):
    print(p[i][0],p[i][1])
```

    3
    7
    1 3
    1 2
    3 2
    1 3
    2 1
    2 3
    1 3
    


```python
# 11729 (히노이 탑 이동 순서)-2
def h(a,b,c):c>1!=h(a,a^b,c-1);print(a,b);c>1!=h(a^b,b,c-1)
c=int(input());print(2**c-1);h(1,3,c)
```

    3
    7
    1 3
    1 2
    3 2
    1 3
    2 1
    2 3
    1 3