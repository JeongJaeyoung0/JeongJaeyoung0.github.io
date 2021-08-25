---
layout: post
title: "[Coding test] Programmers_level 1_소수 찾ㅣ"
subtitle: "ProgrammersLevel-1-48"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/728210c06a19f6946519e8402e5dfcbeb853f894/210825_Programmers_level%201_%E1%84%89%E1%85%A9%E1%84%89%E1%85%AE%20%E1%84%8E%E1%85%A1%E1%86%BD%E1%84%80%E1%85%B5.ipynb)

***

# programmers_level 1_소수 찾기
### 1부터 n 사이에 있는 소수의 개수를 반환


```python
def solution(n):
    t=[True for i in range(n+1)] # 모든 수 True로 전환
    # 에라토스테네스의 체 (소수를 찾는 방법)
    for i in range(2,int(n**0.5)+1): # 2부터 n^0.5+1 까지만 확인
        if t[i]==True: # i가 소수인 경우
            a=2
            while i*a<=n:
                t[i*a]=False # i의 배수는 False
                a+=1
    return sum(t)-2 # True를 합하고 0과 1을 빼준 후 return
```


```python
solution(10)
```




    4




```python
solution(5)
```





    3
