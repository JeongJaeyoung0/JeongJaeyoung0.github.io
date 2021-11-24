---
layout: post
title: "[Coding test] Baekjoon_level 8_기본 수학 1-2"
subtitle: "BaekjoonLevel8-2"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/2d1149270b3d9b3ec623b4be49d5cdd30b5ea873/210602_Baekjoon_coding%20test_level%208_%EA%B8%B0%EB%B3%B8%20%EC%88%98%ED%95%99%201-2.ipynb)

***

2021.06.02
# coding test_Baekjoon_level 8_기본 수학 1-2


```python
# 2775 (부녀회장이 될테야)-1
t=int(input())
apart=[[0]*15 for _ in range(15)]
for i in range(15):
    apart[0][i]=i
for _ in range(t):
    k=int(input())
    n=int(input())
    if apart[k][n]!=0:
        print(apart[k][n])
        continue
    for a in range(k+1):
        for b in range(n+1):
            if apart[a][b]==0:
                for c in range(b+1):
                    apart[a][b]+=apart[a-1][c]
    print(apart[k][n])
```

    2
    1
    3
    6
    2
    3
    10
    


```python
# 2775 (부녀회장이 될테야)-2
import math
i=input
for n in[int]*int(i()):k=n(i());print(math.comb(k+n(i()),k+1))
```

    2
    1
    3
    6
    2
    3
    10
    


```python
# 2839 (설탕 배달)
i=int(input())
b=sorted([a if (i-a*5)%3==0 else -1 for a in range(i//5+1)[::-1]])[-1]
if b==-1:n=-1
else:n=b+(i-5*b)//3
print(n)
```

    11
    3
    


```python
# 10757 (큰 수 A+B)
print(sum(map(int,input().split())))
```

    9223372036854775807 9223372036854775808
    18446744073709551615
    


```python
# 1011 (Fly me to the Alpha Centauri)-1
exec("""x,y=map(int,input().split())
k=y-x
a=(y-x)/2
n=1
p=0
while a>0:
    if a<=n:
        if a*2<=n:p=(n-1)*2+1;a=0
        else:p=n*2;a=0
    a-=n
    n+=1
print(p);"""*int(input()))
```

    3
    0 3
    3
    1 5
    3
    45 50
    4
    


```python
# 1011 (Fly me to the Alpha Centauri)-2
for i in[int]*int(input()):x,y=input().split();print(i(2*(i(y)-i(x)-.5)**.5))
```

    3
    0 3
    3
    1 5
    3
    0 7
    5