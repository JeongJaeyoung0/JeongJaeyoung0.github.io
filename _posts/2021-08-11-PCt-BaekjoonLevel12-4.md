---
layout: post
title: "[Coding test] Baekjoon_level 12_정렬-4"
subtitle: "BaekjoonLevel12-4"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/38a6a1109a5191407e7aea4ef66f2ea838691d3a/210614_Baekjoon_coding%20test_level%2012_%EC%A0%95%EB%A0%AC-4.ipynb)

***

### 2021.06.14

# coding test_Baekjoon_level 12_정렬-4


```python
# 1181 (단어 정렬)-1
a=set([input() for _ in[0]*int(input())])
b=[[len(i),i]for i in a]
b.sort(key=lambda x:x[1])
b.sort(key=lambda x:x[0])
for i in b:print(i[1])
```

    5
    abc
    ab
    a
    az
    za
    a
    ab
    az
    za
    abc
    


```python
# 1181 (단어 정렬)-2
print(*sorted(sorted({*eval("input(),"*int(input()))}),key=len))
```

    3
    ab
    a
    a
    a ab
    


```python
# 10814 (나이순 정렬)-1
a=[[int(i),j] for i, j in [input().split() for _ in[0]*int(input())]]
a.sort(key=lambda x:x[0])
for i in a:print(*i)
```

    3
    21 Jun
    21 Do
    20 Sun
    20 Sun
    21 Jun
    21 Do
    


```python
# 10814 (나이순 정렬)-2
print(*sorted(eval("input(),"*int(input())),key=lambda x:int(x.split()[0])))
```

    3
    21 J
    21 D
    20 S
    20 S 21 J 21 D
    


```python
# 18870 (좌표 압축)-1
# 시간초과
import sys
int(sys.stdin.readline())
a=list(map(int,sys.stdin.readline().split()))
b=list(set(a))
b.sort()
for i in range(len(a)):print(b.index(a[i]),end=' ')
```


```python
# 18870 (좌표 압축)-2
int(input())
a=list(map(int,input().split()))
b=list(sorted(set(a)))
b={b[i]:i for i in range(len(b))}
print(*[b[i] for i in a])
```

    5
    2 4 -10 4 -9
    2 3 0 3 1
    


```python
# 18870 (좌표 압축)-3
input()
a=[*map(int,input().split())]
b=dict(zip(sorted({*a}),range(9**9)))
print(*(b[i]for i in a))
```

    5
    2 4 -10 4 -9
    2 3 0 3 1