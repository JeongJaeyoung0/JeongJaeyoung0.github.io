---
layout: post
title: "[Coding test] Programmers_level 2_다음 큰 숫자"
subtitle: "ProgrammersLevel-2-12"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 자연수 n의 2진수의 1의 개수가 같으며, n보다는 크지만 가장 작은 수를 반환

```python
def solution(n):
    rev = bin(n)[:1:-1] # n을 2진수로 변환 후 역순으로 바꾸고 0b를 제외
    zer = rev.find('1') # 역순에서 0이 연속되는 개수
    one = rev[zer:].find('0') # 첫 1부터 1이 연속되는 개수
    if one == -1: # find('0')이 검출되지 않을 경우 -1이 반환됨 (즉, 0이 없을 경우)
        return int('10' + rev[:-1], 2) # 잴 앞의 1이 +1되어서 10이되고, 뒤에 나머지 1이 붙고, 10진화하여 반환
    return int(rev[:zer+one:-1] + '10' + '0'*zer + '1'*(one-1), 2) # 두 번째 1의 위치 -2 + 두 번째 1이 '10' + 0의 개수 + 1의 개수 (1이 우측으로 쏠리게됨)를 10진화하여 반환 
```

```python
>>> solution(78)
83

>>> solution(15)
23
```