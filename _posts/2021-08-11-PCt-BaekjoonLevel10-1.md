---
layout: post
title: "[Coding test] Baekjoon_level 10_재귀-1"
subtitle: "BaekjoonLevel10-1"
categories: python
tags: codingTestPython
comments: true
---

* `math.factorial()` : 팩토리얼

```python
>>> import math
>>> math.factorial(5)
    Out: 120   # 1*2*3*4*5
```

* `math.log(x,y)` : 로그

```python
>>> import math
>>> math.log(27,3)
    Out: 3.0   # n^3=27
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/7a4893fa45be7c8da3ed0d23c4d6597c683cd1a0/210607_Baekjoon_coding%20test_level%2010_%EC%9E%AC%EA%B7%80-1.ipynb)

***

2021.06.07
# coding test_Baekjoon_level 10_재귀-1


```python
# 10872 (팩토리얼)-1
import math
print(math.factorial(int(input())))
```

    0
    1
    


```python
# 10872 (팩토리얼)-2
f=a=1;exec('f*=a;a+=1;'*int(input()));print(f)
```

    5
    120
    


```python
# 10870 (피보나치 수 5)-1
a=[0,1]
n=int(input())
for i in range(n):
    b=a[i]+a[i+1]
    a.append(b)
print(a[n])
```

    10
    55
    


```python
# 10870 (피보나치 수 5)-2
a=0;b=1;exec("a,b=b,a+b;"*int(input()));print(a)
```

    2
    1
    


```python
# 2447 (별 찍기-10)-1
def s(N,A):
    T=3**N
    B=range(int(T/3),int(2*T/3))
    C=[i for i in range(len(A)) if i%T in B]
    for X in C:
        for Y in C:
            A[X][Y]=' '
    N-=1
    if N!=0:
        return s(N,A)
    else:
        return A

n=int(input())
a=[['*' for c in range(n)] for r in range(n)]
b=s(int(n**(1/3)),a)

p=''
for i in range(len(b)):
    print(''.join(b[i]))
```

    81
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    * *   * *         * *   * ** *   * *         * *   * ** *   * *         * *   * *
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    ***   ******   ******   ***                           ***   ******   ******   ***
    * *   * ** *   * ** *   * *                           * *   * ** *   * ** *   * *
    ***   ******   ******   ***                           ***   ******   ******   ***
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    *********         *********                           *********         *********
    * ** ** *         * ** ** *                           * ** ** *         * ** ** *
    *********         *********                           *********         *********
    ***   ***         ***   ***                           ***   ***         ***   ***
    * *   * *         * *   * *                           * *   * *         * *   * *
    ***   ***         ***   ***                           ***   ***         ***   ***
    *********         *********                           *********         *********
    * ** ** *         * ** ** *                           * ** ** *         * ** ** *
    *********         *********                           *********         *********
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    ***   ******   ******   ***                           ***   ******   ******   ***
    * *   * ** *   * ** *   * *                           * *   * ** *   * ** *   * *
    ***   ******   ******   ***                           ***   ******   ******   ***
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    * *   * *         * *   * ** *   * *         * *   * ** *   * *         * *   * *
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    


```python
import math
```


```python
math.log(27,3)
```




    3.0




```python
# 2447 (별 찍기-10)-2
import math
def s(N,A):
    T=3**N
    B=range(int(T/3),int(2*T/3))
    C=[i for i in range(len(A)) if i%T in B]
    for X in C:
        for Y in C:
            A[X][Y]=' '
    N-=1
    if N!=0:
        return s(N,A)
    else:
        return A

n=int(input())
a=[['*' for c in range(n)] for r in range(n)]
b=s(int(round(math.log(n,3))),a)

p=''
for i in range(len(b)):
    print(''.join(b[i]))
```

    9
    *********
    * ** ** *
    *********
    ***   ***
    * *   * *
    ***   ***
    *********
    * ** ** *
    *********
    


```python
# 2447 (별 찍기-10)-3
n=int(input());s='*'
while n>1:
    t=[i*3 for i in s]
    s=t+[i+' '*len(i)+i for i in s]+t
    n//=3
print('\n'.join(s))
```

    81
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    * *   * *         * *   * ** *   * *         * *   * ** *   * *         * *   * *
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    ***   ******   ******   ***                           ***   ******   ******   ***
    * *   * ** *   * ** *   * *                           * *   * ** *   * ** *   * *
    ***   ******   ******   ***                           ***   ******   ******   ***
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    *********         *********                           *********         *********
    * ** ** *         * ** ** *                           * ** ** *         * ** ** *
    *********         *********                           *********         *********
    ***   ***         ***   ***                           ***   ***         ***   ***
    * *   * *         * *   * *                           * *   * *         * *   * *
    ***   ***         ***   ***                           ***   ***         ***   ***
    *********         *********                           *********         *********
    * ** ** *         * ** ** *                           * ** ** *         * ** ** *
    *********         *********                           *********         *********
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    ***   ******   ******   ***                           ***   ******   ******   ***
    * *   * ** *   * ** *   * *                           * *   * ** *   * ** *   * *
    ***   ******   ******   ***                           ***   ******   ******   ***
    ***************************                           ***************************
    * ** ** ** ** ** ** ** ** *                           * ** ** ** ** ** ** ** ** *
    ***************************                           ***************************
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    * *   * *         * *   * ** *   * *         * *   * ** *   * *         * *   * *
    ***   ***         ***   ******   ***         ***   ******   ***         ***   ***
    *********         ******************         ******************         *********
    * ** ** *         * ** ** ** ** ** *         * ** ** ** ** ** *         * ** ** *
    *********         ******************         ******************         *********
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    * *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * ** *   * *
    ***   ******   ******   ******   ******   ******   ******   ******   ******   ***
    *********************************************************************************
    * ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** ** *
    *********************************************************************************