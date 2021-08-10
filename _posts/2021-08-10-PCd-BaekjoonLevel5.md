---
layout: post
title: "[Coding test] Baekjoon_level 5_1차원 배열"
subtitle: "BaekjoonLevel5"
categories: python
tags: codingtest
comments: true
---

```python
>>> a, *b, c= [1,2,3,4,5]   # *를 붙이면 남는 리스트들 전부

>>> print(a)

    Out: 1

>>> print(b)

    Out: [2,3,4]

>>> print(b)

    Out: 5
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/c4fb56fd8930f0c7c4287380e004fe549dad3415/210526_Baekjoon_coding%20test_level%203_for%EB%AC%B8.ipynb)

***

2021.05.28
# coding test_Baekjoon_level 5_1차원 배열


```python
# 10818 (최소, 최대)-1
b=int(input())-1
a=list(map(int,input().split()))
a.sort()
print(a[0],a[b])
```

    5
    20 10 35 30 7
    7 35
    


```python
# 10818 (최소, 최대)-2
print(min(a:=[*map(int,[*open(0)][1].split())]),max(a))
```


```python
# 2562 (최댓값)-1
# 9개의 수 중 최대값은 얼마이며, 그 자리수는 몇인가?
a=0
for i in range(9):
    b=int(input())
    if a<b:a=b;n=i+1
print(a,n)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    9 9
    


```python
# 2562 (최댓값)-2
print(*max((int(input()),i+1)for i in range(9)))
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    9 9
    


```python
# 2577 (숫자의 개수)-1
# 3개의 숫자를 모두 곱한 값의 숫자들의 중복 갯수?
a=str(eval('*'.join([input()for i in range(3)])))
for b in range(10):print(a.count(str(b)))
```

    150
    266
    427
    3
    1
    0
    2
    0
    0
    0
    2
    0
    0
    


```python
# 2577 (숫자의 개수)-2
# +?
b=0;exec('a=1'+'*int(input())'*3+';print(str(a).count(str(b)));b+=1'*10)
```

    123
    456
    789
    0
    0
    2
    2
    3
    1
    0
    0
    0
    0
    


```python
# 3052 (나머지)-1
# 10개의 수를 42로 나누었을 때 나머지 값이 다른 갯수가 몇개?
print(len(set(int(input())%42for _ in range(10))))
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    10
    


```python
# 3052 (나머지)-2
print(len({*eval('int(input())%42,'*10)}))
```

    42
    84
    252
    420
    840
    126
    42
    84
    420
    126
    1
    


```python
# 1546 (평균)
# n개의 숫자 중, 최댓값을 기준으로 나머지 수를 x/최댓값*100일 경우 전체 평균은?
a=int(input())
b=input().split()
c=max(b)
eval('+'.join([str(int(i)/int(c)*100)for i in b]))/a
```

    5
    1 10 5 2 20
    




    152.0




```python
b
```




    ['1', '10', '5', '2', '20']




```python
max(b)
```




    '5'




```python
c
```




    '5'




```python
c=0
```


```python
[i for i in b if c<int(i)]
```




    ['1', '10', '5', '2', '20']




```python

```


```python
# 1546 (평균)-1
# n개의 숫자 중, 최댓값을 기준으로 나머지 수를 x/최댓값*100일 경우 전체 평균은?
a=int(input())
b=list(map(int,input().split()))
c=max(b)
print(eval('+'.join([str(i/c*100)for i in b]))/a)
```

    5
    1 2 4 8 16
    38.75
    


```python
# 1546 (평균)-2
input()
*a,=map(int,input().split())
print(sum(a)*100/max(a)/len(a))
```

    4
    1 100 100 100
    75.25
    


```python

```


```python

```


```python
# 8958 (OX퀴즈)-1
exec(' input()  ;'*int(input))
```


```python
test = 'OOXXOXXOOO'
```


```python
for i in test:
    if i=='O':
        if i[-1]=='O'
        a=1
```




    'O'