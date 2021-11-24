---
layout: post
title: "[Coding test] Programmers_level 1_음양 더하기"
subtitle: "ProgrammersLevel-1-10"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/8ab46f16c55415e92875a48f3bfff227460d13da/210624_Programmers_level%201_%EC%9D%8C%EC%96%91%20%EB%8D%94%ED%95%98%EA%B8%B0.ipynb)

***

# Programmers_level 1_음양 더하기
### 정수 배열과 부호를 차례로 담은 불리언 배열로 실제 정수의 합을 출력


```python
def solution(absolutes, signs):
    return sum([-a if s==0 else a for a, s in zip(absolutes, signs)])   # True일 경우 그대로, False일 경우 음수로 변경하여 전체를 sum
```


```python
solution([4,7,12], [True,False,True])
```




    9




```python
solution([1,2,3], [False,False,True])
```




    0