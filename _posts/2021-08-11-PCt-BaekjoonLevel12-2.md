---
layout: post
title: "[Coding test] Baekjoon_level 12_정렬-2"
subtitle: "BaekjoonLevel12-2"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/4921d5274180f8eb3376578971c6a6c979a2c954/210612_Baekjoon_coding%20test_level%2012_%EC%A0%95%EB%A0%AC-2.ipynb)

***

2021.06.12
# coding test_Baekjoon_level 12_정렬-2


```python
#2108 (통계학)-1
import collections
import sys

input=sys.stdin.readline
n=int(input())
sum=0
a=[]

if n==1:b=int(input());exec("print(b);"*3);print(0);sys.exit()

for _ in range(n):
    b=int(int(input()))
    a.append(b)
    sum+=b

a.sort()
print(round(sum/n))
print(a[int((len(a)-1)/2)])
c = collections.Counter(a)
c = sorted(c.items(), key=lambda x:(-x[1], x[0]))
if c[0][1]==c[1][1]:print(c[1][0])
else:print(c[0][0])
print(a[-1]-a[0])
```


```python
#2108 (통계학)-2
from statistics import*
n,*l=map(int,open(0))
print('%.0f'%mean(l),median(l),sorted(multimode(l))[:2][-1],max(l)-min(l))
```