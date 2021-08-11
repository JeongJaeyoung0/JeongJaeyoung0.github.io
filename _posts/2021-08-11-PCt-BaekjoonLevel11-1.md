---
layout: post
title: "[Coding test] Baekjoon_level 11_브루트 포스-1"
subtitle: "BaekjoonLevel11-1"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/dbf077a16c2237b312758af7ab6969d601f2aee6/210609_Baekjoon_coding%20test_level%2011_%EB%B8%8C%EB%A3%A8%ED%8A%B8%20%ED%8F%AC%EC%8A%A4-1.ipynb)

***

2021.06.09
# coding test_Baekjoon_level 11_브루트 포스-1


```python
# 2798 (블랙잭)-1
n,k=input().split()
n=int(n)
m=list(map(int,input().split()))
s=0
while n>2:
    for i in m[-n+1:-1]:
        a=m.index(i)
        for j in m[a+1:]:
            b=m[-n]+i+j
            if int(k)>=b>s:s=b
    n-=1
print(s)
```

    10 500
    93 181 245 214 315 36 185 138 216 295
    497
    


```python
# 2798 (블랙잭)-2
from itertools import*
[n,k],m=eval('map(int,input().split()),'*2)
print(max(i for i in map(sum,combinations(m,3)) if i<=k))
```

    5 21
    5 6 7 8 9
    21
    


```python
# 2231 (분해합)-1
a,b=0,1
n=int(input())
while b==1:
    a+=1
    if n==a+sum(map(int,str(a))):print(a);b=0
    if n<a:print('0');b=0
```

    1
    0
    


```python
# 2231 (분해합)-2
n=int(input())
print([*[i for i in range(n) if n==i+sum(map(int,str(i)))],0][0])
```


```python
# 7568 (덩치)-1
x=[];exec("x+=[[i for i in map(int,input().split())]];"*int(input()))
for i in x:
    a=1
    for j in x:
        if i[0]<j[0] and i[1]<j[1]:
            a+=1
    print(a)
```

    5
    55 185
    58 183
    88 186
    60 175
    46 155
    2
    2
    1
    2
    5
    


```python
# 7568 (덩치)-2
*x,=eval(int(input())*'input().split(),')
print(*[sum((a<c)*(b<d)for c,d in x)+1for a,b in x])
```

    5
    55 185
    58 183
    88 186
    60 175
    46 155
    2 2 1 2 5