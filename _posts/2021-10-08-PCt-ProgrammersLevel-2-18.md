---
layout: post
title: "[Coding test] Programmers_level 2_숫자의 표현"
subtitle: "ProgrammersLevel-2-18"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 자연수 n이 매개변수로 주어질 때, 연속된 자연수들로 n을 표현하는 방법의 수를 반환

```python
def solution(n):
    answer = 1 # n = n 이기 때문에 방법 수를 1부터 시작
    for i in range(1, n): # 1부터 n전 까지 for문
        j = i # j = i
        s = 0 # 합을 계산할 변수
        while s <= n: # 합이 n 이하일 경우 while문
            j += 1 # j를 1씩 증가
            s = j*-~j//2 - (i-1)*-~(i-1)//2 # 합 = 연속되는 마지막 자연수까지 등차수열 - (i-1) 까지의 등차수열
            if s == n: # 합이 n과 같을 경우
                answer += 1 # 방법 수 +1
    return answer
```

```python
>>> solution(15)
4
```