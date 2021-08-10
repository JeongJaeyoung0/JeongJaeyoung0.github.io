---
layout: post
title: "[Coding test] Baekjoon_level 2_if문"
subtitle: "BaekjoonLevel2"
categories: python
tags: codingtest
comments: true
--- 
test
``` python
>>> print(*['A','B']) # 프린트 할 때, 리스트 앞에 * 입력시 리스트가 풀려서 출력됨

    Out: A B

>>> print(+[3>2]) # 프린트 할 때, + 입력시 불리언 값을 0, 1로 출력됨 (False: 0, True: 1)

    Out: 1
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/e87fc682f2814b3d5bac72361c99d56f09cfe4fe/210525_Baekjoon_coding%20test_level%202.ipynb)

***

2021.05.25
# coding test_Baekjoon_level 2_if문


```python
# 1330 (두 수 비교하기)-1
a,b=map(int,input().split())
if a>b:print('>')
elif a<b:print('<')
else:print('==')
```

    1 2
    <
    


```python
# 1330 (두 수 비교하기)-2
a,b=map(int,input().split())
print(['<>'[a>b],'=='][a==b])
```

    2 1
    >
    


```python
# 9498 (시험 성적)-1
a=int(input())
print([*[[*[['FD'[59<a],'C'][69<a]],'B'][79<a]],'A'][89<a])
```

    100
    A
    


```python
# 9498 (시험 성적)-2
print('FFFFFFDCBAA'[int(input())//10])
```

    40
    F
    


```python
# 2753 (윤년)-1
# 4의 배수 and 100의 배수가 아닌 or 400의 배수
a=int(input());print(+(a%400<1or a%4<1and a%100>0))
```

    2021
    0
    


```python
# 2753 (윤년)-2
a=int(input());print(+((a%100or a//100)%4<1))
```

    2024
    1
    


```python
2010%100
```




    10




```python
2010//100
```




    20




```python
10 or 20
```




    10




```python
20 or 10
```




    20




```python
0 or 10
```




    10




```python
10 or 0
```




    10




```python
# 14681 (사분면 고르기)-1
x,y=int(input()),int(input());print(['41'[y>0],'32'[y>0]][x<0])
```

    -12
    -5
    3
    


```python
# 14681 (사분면 고르기)-2
print("3421"[input()>"0"::2][input()>"0"])
```

    12
    -5
    4
    


```python
# 2884 (알람 시계)-1
# 입력 시간보다 45분 전
h,m=map(int,input().split())
print(*[[(h+23,m+15),(h-1,m+15)][h>0],(h,m-45)][m>44])
```

    0 44
    23 59
    


```python
# 2884 (알람 시계)-2
h,m=map(int,input().split())
print((h-(m<45))%24,(m-45)%60)
```

    0 45
    0 0
    
