---
layout: post
title: "[Coding test] Programmers_level 1_정수 제곱근 판별"
subtitle: "ProgrammersLevel-1-35"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/4103c396232dc951c706987200902c4cbf52f037/210720_Programmers_level%201_%EC%A0%95%EC%88%98%20%EC%A0%9C%EA%B3%B1%EA%B7%BC%20%ED%8C%90%EB%B3%84.ipynb)

***

# Programmers_level 1_정수 제곱근 판별
### 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하여 제곱이라면 x+1의 제곱을 반환하고, 아니라면 -1을 반환.


```python
def solution(n):
    root = n**0.5                                       # 루트n
    return (root+1)**2 if str(root)[-1] == '0' else -1  # 소수점이 0이면 제곱근으로 판별
```


```python
solution(121)
```




    144.0




```python
solution(3)
```




    -1