---
layout: post
title: "[Coding test] Programmers_level 2_소수 찾기"
subtitle: "ProgrammersLevel-2-23"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수 개수를 반환

```python
def prime_number(n):
    # 0, 1은 소수 아님
    if n == 0 or n == 1:
        return False
    # 2부터 n^2+1 까지만 확인
    for i in range(2,int(n**0.5)+1):
        # 나누어 떨어질 경우 소수 아님
        if n % i == 0:
            return False
    # for 문이 다 돌아도 False이 아닐 경우 소수
    return True

def solution(numbers):
    from itertools import permutations
    
    # 문자 하나씩 잘라서 리스트
    num = list(numbers)
    # 문자 개수만큼 permutations
    per = sum([list(permutations(num, i+1)) for i in range(len(num))], [])
    # join하여 중복 제거(set) 후 다시 리스트
    nums = list(set([int(''.join(j)) for j in per]))
    # 소수가 맞는지 확인 하고, 소수가 맞는 개수 반환
    return sum([prime_number(num) for num in nums])
```

```python
>>> solution('17')
3
>>> solution('011')
2
```