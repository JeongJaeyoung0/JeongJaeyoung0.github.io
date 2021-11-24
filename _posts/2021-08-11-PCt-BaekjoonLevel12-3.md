---
layout: post
title: "[Coding test] Baekjoon_level 12_정렬-3"
subtitle: "BaekjoonLevel12-3"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7e45837cd346c87c1ecddc502a13983c4f74725/210613_Baekjoon_coding%20test_level%2012_%EC%A0%95%EB%A0%AC-3.ipynb)

***

2021.06.13
# coding test_Baekjoon_level 12_정렬-3


```python
# 1427 (소트인사이드)-1
print(''.join(sorted(input(),reverse=True)))
```

    2143
    4321
    


```python
# 1427 (소트인사이드)-2
print(*sorted(input())[::-1],sep='')
```

    2143
    4321
    


```python
# 11650 (좌표 정렬하기)-1
# 시간초과
a=[];exec("a+=[input()];"*int(input()))
a.sort(key=lambda x:x[1])
a.sort(key=lambda x:x[0])
for i in sorted(a):print(i)
```

    3
    100 101
    101 99
    99 100
    100 101
    101 99
    99 100
    


```python
# 11650 (좌표 정렬하기)-2
a=[]
for _ in range(int(input())):
    x,y = map(int,input().split())
    a.append((x,y))
a.sort(key=lambda x:x[1])
a.sort(key=lambda x:x[0])
for i in a:print(i[0],i[1])
```

    3
    99 101
    99 100
    100 101
    99 100
    99 101
    100 101
    


```python
# 11650 (좌표 정렬하기)-3
for a in sorted([*map(int,input().split())]for _ in[0]*int(input())):print(*a)
```

    3
    99 101
    99 100
    100 99
    99 100
    99 101
    100 99
    


```python
# 11651 (좌표 정렬하기 2)-1
a=[]
for _ in range(int(input())):
    x,y = map(int,input().split())
    a.append((x,y))
a.sort(key=lambda x:x[0])
a.sort(key=lambda x:x[1])
for i in a:print(i[0],i[1])
```

    5
    0 4
    1 2
    1 -1
    2 2
    3 3
    1 -1
    1 2
    2 2
    3 3
    0 4
    


```python
# 11651 (좌표 정렬하기 2)-2
for a in sorted([*map(int,input().split()[::-1])]for _ in[0]*int(input())):print(*a[::-1])
```

    5
    0 4
    1 2
    1 -1
    2 2
    3 3
    1 -1
    1 2
    2 2
    3 3
    0 4