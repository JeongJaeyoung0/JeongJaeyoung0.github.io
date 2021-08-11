---
layout: post
title: "[Coding test] Baekjoon_level 9_기본 수학 2-1"
subtitle: "BaekjoonLevel9-1"
categories: python
tags: codingtest
comments: true
---

* `all` 함수: 모든 요소가 True일 경우 True로 반환

```python
>>> all([1,1,1,])

     Out: True

>>> all[(1,0,1])

     Out: False
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/8a4de9218ae325bdc93ea0b7a4435decf5462c18/210604_Baekjoon_coding%20test_level%209_%EA%B8%B0%EB%B3%B8%20%EC%88%98%ED%95%99%202-1.ipynb)

***

2021.06.04
# coding test_Baekjoon_level 9_기본 수학 2-1


```python
# 1978 (소수 찾기)-1
import math

def prime_number(n):
    t=[True for i in range(n+1)]
    for i in range(2,int(math.sqrt(n))+1):
        if t[i]==True:
            a=2
            while i*a<=n:
                t[i*a]=False
                a+=1
    return[i for i in range(2,n+1) if t[i]]

input()
a=set(map(int,input().split()))
b=set(prime_number(max(a)))
print(len(a&b))
```

    4
    1 3 5 7
    3
    


```python
# 1978 (소수 찾기)-2
input();print(sum(all(i%s for s in range(2,i))*i>1for i in map(int,input().split())))
```


```python
# 2581 (소수)-1
import math

def prime_number(n):
    t=[True for i in range(n+1)]
    for i in range(2,int(math.sqrt(n))+1):
        if t[i]==True:
            a=2
            while i*a<=n:
                t[i*a]=False
                a+=1
    return[i for i in range(2,n+1) if t[i]]

m=int(input())
n=int(input())
p=prime_number(n)
a=[i for i in p if m<=i]
if a==[]:print(-1)
else:print(sum(a),a[0],sep='\n')
```

    60
    100
    620
    61
    


```python
# 2581 (소수)-2
m,n=int(input()),int(input());p=[i for i in range(m,n+1) if len([a for a in range(1,i+1) if i%a==0])==2];print(f'{sum(p)}\n{p[0]}' if p else -1)
```

    60
    100
    620
    61
    


```python
# 11653 (소인수분해)-1
n=int(input())
a=[]
while n>1:b=[i for i in range(2,n+1) if n%i==0][0];a+=[b];n=n//b
for s in a:print(s)
```

    72
    2
    2
    2
    3
    3
    


```python
# 11653 (소인수분해)-2
n=int(input());a=2
while n>1:
    if n%a:a+=1
    else:print(a);n/=a
```

    10
    2
    5
    


```python
# 1929 (소수 구하기)-1
# 시간 초과
m,n=input().split()
for i in [i for i in range(int(m),int(n)+1) if len([a for a in range(1,i+1) if i%a==0])==2]:print(i)
```

    1 10
    2
    3
    5
    7
    


```python
# 1929 (소수 구하기)-2
import math

def prime_number(n):
    t=[True for i in range(n+1)]
    for i in range(2,int(math.sqrt(n))+1):
        if t[i]==True:
            a=2
            while i*a<=n:
                t[i*a]=False
                a+=1
    return[i for i in range(2,n+1) if t[i]]

m,n=input().split()
p=prime_number(int(n))
for i in p:
    if int(m)<=i:
        print(i)
```

    3 16
    3
    5
    7
    11
    13
    


```python
# 1929 (소수 구하기)-3
m,n=map(int,input().split());p=[*range(n+1)]
for i in p:
    if 1<i:p[i*i::i]=-(i+~n//i)*[0]
    if 1<i>=m:print(i)
```

    10 20
    11
    13
    17
    19
    


```python
# 4948 (베르트랑 공준)-1
# 시간 초과
while (n:=int(input()))!=0:p=[i for i in range(n+1,n*2+1) if len([a for a in range(1,i+1) if i%a==0])==2];print(len(p))
```

    1
    1
    10
    4
    13
    3
    100
    21
    1000
    135
    10000
    1033
    0
    


```python
# 4948 (베르트랑 공준)-2
while (n:=int(input()))!=0:
    n+=1;m=n*2-1
    p=[*range(m)]
    for i in p:
        if 1<i:p[i*i::i]=-(i+~(m-1)//i)*[0]
    print(len([a for a in p if 1<a>=n]))
```

    1000
    135
    10000
    1033
    100000
    8392
    0
    


```python
# 4948 (베르트랑 공준)-3
z=123456
a,b=1,[1]*(z+1)
while(a:=a+1)*a<z+1:
    if b[a]:b[2*a::a]=[0]*(z//a-1)
while(n:=int(input()))>0:
    print(sum(b[n+1:2*n+1]))
```

    1
    1
    10
    4
    0
    


```python

```


```python
int(input())
```

    5
    




    5




```python
list(map(int,input().split()))
```

    1 2 3 4 5
    




    [1, 2, 3, 4, 5]