---
layout: post
title: "[Coding test] Baekjoon_level 3_for문"
subtitle: "BaekjoonLevel3"
categories: python
tags: codingtest
comments: true
---

* `*a*-~b`

    ~ 는 b 값을 *(-1)+(1)을 의미

    &#45; 는 뒤의 값을 음수로 바꾸는 의미

* `*n*-~n//10` : 1 ~ n 까지의 합을 구할 때 사용

* `eval()` : str의 수를 넣으면 그대로 실행하여 결과 출력

```python
>>> eval('1+2')

    Out: 3
```

* `exec( ' ' )` : str의 문을 넣으면 그대로 실행하여 결과 출력

```python
>>> a=1; exec('print(2*a)')

    Out: 2
```

```python
>>> a=1; exec('print(f "2*{a}") ; a+=1 ;'*4)     # 프린트문 안에서 변수값이 바뀔경우 문자열 앞에 f를 입력

    Out: 2*1 2*2 2*3 2*4
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/c4fb56fd8930f0c7c4287380e004fe549dad3415/210526_Baekjoon_coding%20test_level%203_for%EB%AC%B8.ipynb)

***

2021.05.26
# coding test_Baekjoon_level 3_for문


```python
# 2739 (구구단)-1
x=int(input())
for y in range(1,10):print(x,'*',y,'=',x*y)
```

    2
    2 * 1 = 2
    2 * 2 = 4
    2 * 3 = 6
    2 * 4 = 8
    2 * 5 = 10
    2 * 6 = 12
    2 * 7 = 14
    2 * 8 = 16
    2 * 9 = 18
    


```python
# 2739 (구구단)-2
# exec(): eval은 문자열 속의 산식만 가능하지만, exec는 문도(ex. a=a+1) 가능
x=y=int(input());exec("print(x,'*',y//x,'=',y);y+=x;"*9)
```

    11
    11 * 1 = 11
    11 * 2 = 22
    11 * 3 = 33
    11 * 4 = 44
    11 * 5 = 55
    11 * 6 = 66
    11 * 7 = 77
    11 * 8 = 88
    11 * 9 = 99
    


```python
# 10950 (A+B -3)-1
for i in range(int(input())):
    x,y=input().split()
    print(int(x)+int(y))
```

    5
    1 1
    2
    2 3
    5
    3 4
    7
    9 8
    17
    5 2
    7
    


```python
# 10950 (A+B -3)-2
exec('print(eval("+".join(input())));'*int(input()))
```

    5
    1 1
    2
    2 2
    4
    3 3
    6
    4 4
    8
    5 5
    10
    


```python
# 8393 (n까지 자연수의 합)-1
a=int(input());print((a*a+a)//2)
```

    3
    6
    


```python
# 8393 (n까지 자연수의 합)-2
# ~a: a값을 음수로 바꾸고, -1을 더하는 의미
a=int(input());print((a*-~a)//2)
```

    4
    10
    


```python
# 15552 (빠른 A+B)-1
# sys.stdin: 여러줄 입력 받을 경우 input은 오래 걸림
import sys
for i in range(int(input())):
        a,b=map(int,sys.stdin.readline().split())
        print(a+b)
```


```python
# 15552 (빠른 A+B)-2
import sys
input()
for i in sys.stdin:print(sum(map(int,i.split())))
```


```python
# 2741 (1부터 N까지 출력)-1
for i in range(int(input())):print(i+1)
```

    5
    1
    2
    3
    4
    5
    


```python
# 2741 (1부터 N까지 출력)-2
# 시간 초과
a=1
exec('print(a);a+=1;'*int(input()))
```

    3
    1
    2
    3
    


```python
# 2741 (1부터 N까지 출력)-3
print(*range(1,int(input())+1))
```

    5
    1 2 3 4 5
    


```python
# 2742 (N부터 1까지 출력)-1
for i in list(range(1,int(input())+1))[::-1]:print(i)
```

    5
    5
    4
    3
    2
    1
    


```python
# 2742 (N부터 1까지 출력)-1
print(*range(int(input()),0,-1))
```

    5
    5 4 3 2 1
    


```python
# 11021 (A+B -7)-1
for i in range(1,int(input())+1):
    exec('print("Case #",i,": ",eval("+".join(input())),sep="");')
```

    5
    1 1
    Case #1: 2
    2 3
    Case #2: 5
    3 4
    Case #3: 7
    9 8
    Case #4: 17
    5 2
    Case #5: 7
    


```python
# 11021 (A+B -7)-2
i=1;exec('print(f"Case #{i}:",eval("+".join(input())));i+=1;'*int(input()))
```

    5
    1 1
    Case #1: 2
    2 3
    Case #2: 5
    3 4
    Case #3: 7
    9 8
    Case #4: 17
    5 2
    Case #5: 7
    


```python
# 11021 (A+B -8)-1
i=1;exec('a,b=map(int,input().split());print(f"Case #{i}: {a} + {b} = {a+b}");i+=1;'*int(input()))
```

    5
    1 2
    Case #1: 1 + 2 = 3
    2 3
    Case #2: 2 + 3 = 5
    3 4 
    Case #3: 3 + 4 = 7
    4 5
    Case #4: 4 + 5 = 9
    5 6
    Case #5: 5 + 6 = 11
    


```python
# 11021 (A+B -8)-2
i=1;exec("a=' + '.join(input()[::2]);print(f'Case #{i}:',a,'=',eval(a));i+=1;"*int(input()))
```

    5
    1 1
    Case #1: 1 + 1 = 2
    2 2 
    Case #2: 2 + 2 = 4
    3 3
    Case #3: 3 + 3 = 6
    4 4
    Case #4: 4 + 4 = 8
    5 5
    Case #5: 5 + 5 = 10
    


```python
# 2438 (별 찍기 -1)-1
i=1;exec("print('*'*i);i+=1;"*int(input()))
```

    5
    *
    **
    ***
    ****
    *****
    


```python
# 2438 (별 찍기 -1)-2
for i in range(int(input())):print('*'*-~i)
```

    3
    *
    **
    ***
    


```python
# 2438 (별 찍기 -2)-1
n=int(input())
for i in range(n):print(('*'*-~i).rjust(n))
```

    5
        *
       **
      ***
     ****
    *****
    


```python
# 10871 (X보다 작은 수)-1, 정수 N개가 주어지고, 그 중 X보다 작은 수 출력
n,x=map(int,input().split())
a=[];[a.append(i)for i in map(int,input().split())if x>i];print(*a)
```

    10 5
    1 10 4 9 2 3 8 5 7 6
    1 4 2 3
    


```python
# 10871 (X보다 작은 수)-2
n,x=input().split();print(*(i for i in input().split()if int(x)>int(i)))
```

    10 5
    1 10 4 9 2 3 8 5 7 6
    1 4 2 3
    
