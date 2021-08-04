---
layout: post
title: "[Function] 소수 판별"
subtitle: "PrimeNumber"
categories: python
tags: function
comments: true
---

* 2부터 n까지 소수 리스트 반환하는 함수

<br>

# ● code

***

```python
def prime_number(n): # 소수(2부터 n까지 소수 리스트 반환)
    import math
    
    t=[True for i in range(n+1)] # 모든 수 True로 전환
    
    # 에라토스테네스의 체 (소수를 찾는 방법)
    for i in range(2,int(math.sqrt(n))+1): # 2부터 n^2+1 까지만 확인
        if t[i]==True: # i가 소수인 경우
            a=2
            while i*a<=n:
                t[i*a]=False # i의 배수는 False
                a+=1
                
    return[i for i in range(2,n+1) if t[i]] # True 위치 값만 숫자로 return
```


```python
prime_number(20)
```




    [2, 3, 5, 7, 11, 13, 17, 19]


