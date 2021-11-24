---
layout: post
title: "[Coding test] Baekjoon_level 12_정렬-1"
subtitle: "BaekjoonLevel12-1"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/ac2bac6fadd507c8f8d9ddc9871f121dd5588196/210611_Baekjoon_coding%20test_level%2012_%EC%A0%95%EB%A0%AC-1.ipynb)

***

2021.06.11
# coding test_Baekjoon_level 12_정렬-1


```python
# 2750 (수 정렬하기)
print(*sorted(eval("int(input()),"*int(input()))))
```

    3
    2
    3
    1
    1 2 3
    


```python
# 2751 (수 정렬하기 2)
print(*sorted(map(int,[*open(0)][1:])))
```


```python
# 10989 (수 정렬하기 3)
import sys
input=sys.stdin.readline
a=10001;b=[0]*a
for _ in range(int(input())):b[int(input())]+=1
for i in range(1,a):print(f"{i}\n"*l[i],end="")
```