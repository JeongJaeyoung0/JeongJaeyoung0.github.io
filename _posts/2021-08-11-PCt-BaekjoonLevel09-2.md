---
layout: post
title: "[Coding test] Baekjoon_level 9_기본 수학 2-2"
subtitle: "BaekjoonLevel9-2"
categories: python
tags: codingtest
comments: true
---

* `^`(caret): XOR

|a|b|a xor b|
|:---:|:---:|:---:|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

```python
>>> a=10; b=0
>>> a^b
    Out: 10
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/3bf5c14b6f622276c0e52aa167acd588543bd022/210605_Baekjoon_coding%20test_level%209_%EA%B8%B0%EB%B3%B8%20%EC%88%98%ED%95%99%202-2.ipynb)

***

2021.06.05
# coding test_Baekjoon_level 9_기본 수학 2-2


```python
# 9020 (골드바흐의 추측)-1
# 시간 초과
s=[];o=10000;p=[*range(o+1)]
for i in p:
    if 1<i:p[i*i::i]=-(i+~o//i)*[0]
    if 1<i:s.append(i)
t=int(input())
while t>0:
    n=int(input())
    l=[i for i in range(len(s)) if n-s[i]>1]
    b=[[s[i],s[u]] for i in l for u in l if n-s[i]-s[u]==0]
    print(*(b[(len(b)-1)//2]))
    t-=1
```


```python
# 9020 (골드바흐의 추측)-2
# 시간 초과
import math
n=5100
t=[True for i in range(n+1)]
for i in range(2,int(math.sqrt(n))+1):
    if t[i]==True:
        a=2
        while i*a<=n:
            t[i*a]=False
            a+=1
s=[i for i in range(2,n+1) if t[i]]
t=int(input())
while t>0:
    n=int(input())
    l=[i for i in range(len(s)) if n-s[i]>1]
    b=[[s[i],s[u]] for i in l for u in l if n-s[i]-s[u]==0]
    print(*(b[(len(b)-1)//2]))
    t-=1
```


```python
# 9020 (골드바흐의 추측)-3
def p(n):
    d=[True]*n
    h=int(n**0.5)
    for i in range(2,h+1):
        if d[i]==True:
            for j in range(i+i,n,i):
                d[j]=False
    return [i for i in range(2,n) if d[i]==True]

q=[True]*10000
h=int(10000**0.5)
for i in range(2,h+1):
    if q[i]==True:
        for j in range(i+i,10000,i):
            q[j]=False
q[0]=False
q[1]=False

for j in range(int(input())):
    a=int(input())
    b=p(a+1)
    b.reverse()
    w=a
    for k in b:
        g=a-k
        if q[g] == True:
            m=k-g
            if 0<=m and k>=g:
                x=k
                y=g
    print(f'{y} {x}')
```

    3
    10
    5 5
    10000
    4919 5081
    50
    19 31
    


```python
# 1085 (직사각형에서 탈출)
x,y,w,h=map(int,input().split())
print(min(x,w-x,y,h-y))
```

    6 2 10 3
    


```python
# 3009 (네 번째 점)-1
a=[]
exec("a+=list(map(int,input().split()));"*3)
if a[0]==a[2]:x=a[4]
elif a[0]==a[4]:x=a[2]
else:x=a[0]
if a[1]==a[3]:y=a[5]
elif a[1]==a[5]:y=a[3]
else:y=a[1]
print(f'{x} {y}')
```

    30 20
    10 10
    10 20
    30 10
    


```python
# 3009 (네 번째 점)-2
x=y=0;exec("a,b=map(int,input().split());x^=a;y^=b;"*3)
print(x,y)
```

    30 20
    10 10
    10 20
    30 10