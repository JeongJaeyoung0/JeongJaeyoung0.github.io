---
layout: post
title: "[Coding test] Baekjoon_level 1_입출력과 사칙연산"
subtitle: "BaekjoonLevel1"
categories: python
tags: codingTestPython
comments: true
---

* `eval()` : str의 수를 넣으면 그대로 실행하여 결과 출력
* `''.join()` :  join하면서 ''안의 값을 문자 사이에 입력

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/364b57562b3a0f4b4a9345c7ea907c63d8516346/210525_Baekjoon_coding%20test_level%201.ipynb)

***

2021.05.25
# coding test_Baekjoon_level 1_입출력과 사칙연산


```python
# 2557 (프린트)
print('Hello World!')
print("Hello World!")
print('''Hello World!''')
print("""Hello World!""")
```

    Hello World!
    Hello World!
    Hello World!
    Hello World!
    


```python
# 10718 (프린트)
print('강한친구 대한육군 '*2)
```

    강한친구 대한육군강한친구 대한육군
    


```python
# 10171 (프린트)
print("\    /\ \n )  ( ')\n(  /  )\n \(__)|")
```

    \    /\ 
     )  ( ')
    (  /  )
     \(__)|
    


```python
# 10172 (프린트)
print('|\_/|\n|q p|   /}\n( 0 )"""\ \n|"^"`    |\n||_/=\\\__|')
```

    |\_/|
    |q p|   /}
    ( 0 )"""\ 
    |"^"`    |
    ||_/=\\__|
    


```python
# 1000 (덧셈)
# eval() : str 값을 넣으면 그대로 실행하여 결과 출력
# ''.join() : join하면서 ''안의 값을 문자 사이에 입력
print(eval('+'.join(input())))
```

    1 2
    3
    


```python
# 1001 (뺄셈)
a,b,c=input();print(int(a)-int(c))
```

    3 2
    1
    


```python
# 10998 (곱셈)
a,b,c=input();print(int(a)*int(c))
```

    3 4
    12
    


```python
# 1008 (나눗셈)
a,b,c=input();print(int(a)/int(c))
```

    4 5
    0.8
    


```python
# 10869 (사칙연산, 몫 출력)
a,b=map(int,input().split());print(a+b,a-b,a*b,a//b,a%b)
```

    7 3
    10 4 21 2 1
    


```python
# 10430 (나머지)
a,b,c=map(int,input().split());print(x:=(a+b)%c,x,y:=a*b%c,y)
```

    5 8 4
    1 1 0 0
    


```python
# 2588 (곱셈)
a,b=int(input()),input()
print(*[a*int(p)for p in b][::-1],a*int(b))
```

    472
    385
    2360 3776 1416 181720
