---
layout: post
title: "[Coding test] Programmers_level 2_가장 큰 수"
subtitle: "ProgrammersLevel-2-22"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 반환

```python
def solution(numbers):
    # 문자열로 변환
    numbers = list(map(str, numbers))
    # 6자리수로 반복 ex: [(1, 111111), (20, 202020), (345, 345345), (1000, 100000)]
    num = [(n, n * (6 // len(n))) if n != '1000' else (n, '100000') for n in numbers]
    # 6자리수를 기준으로 내림차순 정렬 
    num.sort(key=lambda x : x[1], reverse=True)
    # 원래의 수를 join하고, 값이 000일 경우도 있기 때문에, 정수형으로 변환 후 다시 문자열로 변환하여 반환
    return str(int(''.join([n[0] for n in num])))
```

```python
>>> solution([6, 10, 2])
"6210"
>>> solution([3, 30, 34, 5, 9])
"9534330"
>>> solution([151, 15, 1])
"151511"
>>> solution([0, 0, 0])
"0"
```