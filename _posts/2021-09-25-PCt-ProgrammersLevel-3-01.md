---
layout: post
title: "[Coding test] Programmers_level 3_N으로 표현"
subtitle: "ProgrammersLevel-3-01"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 1~9의 수를 이용하여 사칙연산으로 number의 값을 만들 수 있는 경우 중 가장 적게 사용 할 수 있는 수의 개수를 반환, 단 8개 초과할 경우 -1을 반환

```python
def solution(N, number):
    arr = [[]] + [[int(str(N) * i)] for i in range(1,9)] # N이 0 ~ 8개의 리스트

    if [number] in arr: # number가 arr에 있을 경우
        return arr.index([number]) # 그 위치(숫자의 개수)를 반환

    for i in range(2, 9): # 숫자 개수
        for j in range(1, i): # 이전 숫자 개수
            for a in arr[j]: # 1 ~ 직전 숫자로 이루어진 리스트
                for b in arr[i-j]: # 직전 ~ 1로 이루어진 리스트 ('i=4', 'a: 1, 2, 3' 'b: 3, 2, 1' 형태로 사용되는 숫자의 개수는 동일)
                    arr[i].append(a + b) # 덧셈
                    arr[i].append(a * b) # 곱셈
                    arr[i].append(a - b) # 뺄셈
                    if 0 != b: # 분모가 0이 아닐 경우
                        arr[i].append(a // b) # 몫
        if number in arr[i]: # number가 i개로 이루어진 arr에 있을 경우
            return i # 사용된 숫자의 개수 리턴
        arr[i] = list(set(arr[i])) # i개로 이루어진 리스트를 집합을 사용하여 중복값 제거
    return -1 # 8개로 이루어진 숫자도 number를 만들 수 없을 경우 -1 리턴
```

```python
>>> solution(5, 12)
4
>>> solution(2, 11)
3
```
