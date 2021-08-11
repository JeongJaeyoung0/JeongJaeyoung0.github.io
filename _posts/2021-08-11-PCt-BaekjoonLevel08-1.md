---
layout: post
title: "[Coding test] Baekjoon_level 8_기본 수학 1-1"
subtitle: "BaekjoonLevel8-1"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/94d94693f0879420c4dc7b8f1f9b587051a9cd3e/210601_Baekjoon_coding%20test_level%208_%EA%B8%B0%EB%B3%B8%20%EC%88%98%ED%95%99%201-1.ipynb)

***

2021.06.01
# coding test_Baekjoon_level 8_기본 수학 1-1


```python
# 1712 (손익분기점)-1
a,b,c=map(int,input().split())
if b>=c:print('-1')
else:print(a//(c-b)+1)
```

    3 2 1
    -1
    


```python
# 1712 (손익분기점)-2
a,b,c=map(int,input().split());print(-(c<=b)or a//(c-b)+1)
```

    2100000000 9 10
    2100000001
    


```python
# 2292 (벌집)-1
a=int(input())-1;c=1
while a>0:a=a-6*c;c+=1
print(c)
```

    58
    5
    


```python
# 2292 (벌집)-2
print(int((int(input())/3-.1)**.5+1.5))
```

    13
    3
    


```python
# 1193 (분수찾기)-1
n=int(input())
m=0
while n>0:m+=1;n-=m
x=m+n
y=1-n
if m%2:print(y,'/',x,sep='')
else:print(x,'/',y,sep='')
```

    14
    2/4
    


```python
# 1193 (분수찾기)-2
n=int(input())
m=0
while n>0:m+=1;n-=m
print("%d/%d"%(1-n,m+n)[::m%2*2-1])
```

    2
    1/2
    


```python
# 2869 (달팽이는 올라가고 싶다)-1
import math
a,b,v=map(int,input().split())
print(math.ceil((v-b)/(a-b)))
```

    2 1 5
    4
    


```python
# 2869 (달팽이는 올라가고 싶다)-2
a,b,v=map(int,input().split())
print(1-(v-a)//(b-a))
```

    100 99 1000000000
    999999901
    


```python
# 10250 (ACM 호텔)-1
exec("""
h,w,n=map(int,input().split())
if n%h==0:x=h;y=n//h
else:x=n%h;y=n//h+1
print(x,'%02d'%(y),sep='');"""*int(input()))
```

    2
    6 12 10
    402
    30 50 72
    1203
    


```python
# 10250 (ACM 호텔)-2
exec('h,w,n=map(int,input().split());print(~-n//h+~-n%h*100+101);'*int(input()))
```

    2
    6 12 10
    402
    30 50 72
    1203