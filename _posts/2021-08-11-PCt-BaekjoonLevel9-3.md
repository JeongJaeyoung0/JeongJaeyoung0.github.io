---
layout: post
title: "[Coding test] Baekjoon_level 9_기본 수학 2-3"
subtitle: "BaekjoonLevel9-3"
categories: python
tags: codingtest
comments: true
---

* `math.pi` : π(파이)

```python
>>> import math
>>> math.pi
```

* 부동실수 오차

```python
>>> 0.1+0.2

    Out: 0.30000000000000004

>>> 0.1+0.2==0.3

    Out: False

>>> import decimal
>>> decimal.Decimal('0.1')+decimal.Decimal('0.2')==decimal.Decimal('0.3')

    Out: True
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/96cb00de8bcc5bc81b0a2aac77565bcdd26fb002/210606_Baekjoon_coding%20test_level%209_%EA%B8%B0%EB%B3%B8%20%EC%88%98%ED%95%99%202-3.ipynb)

***

2021.06.06
# coding test_Baekjoon_level 9_기본 수학 2-3


```python
# 4153 (직각삼각형)-1
a=sorted(list((map(int,input().split()))))
while sum(a)!=0:
    if a[0]**2+a[1]**2==a[2]**2:print('right')
    else:print('wrong')
    a=sorted(list((map(int,input().split()))))
```

    6 8 10
    right
    0 0 0
    


```python
# 4153 (직각삼각형)-2
a=1
while a:a,b,c=sorted(map(int,input().split()));a>0==print('rwirgohntg'[a*a+b*b!=c*c::2])
```

    6 8 10
    right
    0 0 0
    


```python
# 3053 (택시 기하학)-1
import math
r=int(input())
print(r*r*math.pi,2*r*r)
```

    21
    1385.4423602330987 882
    


```python
# 3053 (택시 기하학)-2
r=int(input())**2;print(r*3.14159265359,r*2)
```

    42
    5541.7694409327605 3528
    


```python
# 1002 (터렛)-1
for _ in range(int(input())):
    x,y,r,a,b,c=map(int,input().split())
    d=(((x-a)**2)+((y-b)**2))**.5
    if x==a and y==b and r==c:print(-1)
    elif d==r+c or d==abs(r-c):print(1)
    elif r+c<d or d<abs(r-c) or d==0:print(0)
    else:print(2)
```

    3
    0 0 13 40 0 37
    2
    0 0 3 0 7 4
    1
    1 1 1 1 1 5
    0
    


```python
# 1002 (터렛)-2
exec('x,y,r,a,b,c=map(int,input().split());d=((x-a)**2+(y-b)**2)**.5;print(-1if d==0and r==c else 1if d==r+c or d==abs(r-c) else 0if r+c<d or d<abs(r-c) or d==0else 2);'*int(input()))
```

    3
    0 0 13 40 0 37
    2
    0 0 3 0 7 4
    1
    1 1 1 1 1 5
    0
    


```python
0.1+0.2 == 0.3
```




    False




```python
import decimal
decimal.Decimal('0.1')+decimal.Decimal('0.2')==decimal.Decimal('0.3')
```




    True