---
layout: post
title: "[Coding test] Programmers_level 1_최대공약수와 최소공배수"
subtitle: "ProgrammersLevel-1-32"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/7c506eab42af71d1aaa3223d0c1c7fe26b24cbe7/210717_Programmers_level%201_%EC%B5%9C%EB%8C%80%EA%B3%B5%EC%95%BD%EC%88%98%EC%99%80%20%EC%B5%9C%EC%86%8C%EA%B3%B5%EB%B0%B0%EC%88%98.ipynb)

***

# Programmers_level 1_최대공약수와 최소공배수
### 두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환


```python
# 유클리드 호제법
def solution(n, m):
    for i in range(n):
        if n%(n-i)+m%(n-i) == 0:        # 최대공약수 = n%(n-i)+m%(n-i) == 0
            return [n-i, n*m/(n-i)]     # 최소공약수 = n*m/최대공약수
```


```python
# 약수, 최대공약수, 배수, 최소공배수 풀이
def divisor(num):           # 약수
    return [i for i in range(1,num+1) if num%i==0]  # 나머지가 0이 되는 값 반환

def gcd(a, b):              # 최대공약수
    div_a = divisor(a)      # a의 약수
    div_b = divisor(b)      # b의 약수
    return max([i for i in div_a if i in div_b])    # 공집합의 최대값 반환

def multiple(num, n):       # 배수 (n까지)
    return [num*i for i in range(1,n+1)]

def lcm(a, b):              # 최소공배수
    mul_a = multiple(a, b)  # a의 배수 (b까지)
    mul_b = multiple(b, a)  # b의 배수 (a까지)
    return min([i for i in mul_a if i in mul_b])    # 공집합의 최소값 반환

def solution(n, m):
    return [gcd(n, m), lcm(n, m)]
```


```python
solution(3, 12)
```




    [3, 12]




```python
solution(2, 5)
```




    [1, 10]