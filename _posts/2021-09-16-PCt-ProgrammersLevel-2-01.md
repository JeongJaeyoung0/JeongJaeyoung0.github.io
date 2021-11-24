---
layout: post
title: "[Coding test] Programmers_level 2_124 나라의 숫자"
subtitle: "ProgrammersLevel-2-01"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 10진법 n을 1, 2, 4로 표현 

```python
def solution(n):
    rev_ternary = [] # 3진법으로 변환할 리스트
    while n > 2: # n이 2 초과일 경우
        n, r = divmod(n, 3) # n을 3으로 나눠서 몫은 n, 나머지는 r
        if r == 0: # 나머지가 0일 경우
            rev_ternary.append(r) # 나머지를 리스트에 추가
            n -= 1 # 나머지가 0이란 것은 3의 배수라는 의미이고, 이 경우 3진법으로 10이 반환된다, 하지만 124 나라에서는 0을 표현 할 수 없기 때문에 1을 빼서 나머지가 2가 되게만든다. (요약: 10진법 3은 3진법으로 10이 된다. 이것을 124 나라의 4로 바꾸는 작업)
        else:
            rev_ternary.append(r) # 나머지가 0이 아닐 경우(3의 배수가 아닌경우) 나머지를 리스트에 추가
    if n != 0: # n이 0이 아닐 경우(while문 빠져 나온 후)
        rev_ternary.append(n) # 몫 값을 리스트에 추가
    return ''.join(['4' if i==0 else '1' if i==1 else '2' for i in rev_ternary[::-1]]) # 변환한 것을 역순으로 0은 4, 1은 1, 2는 2로 반환
```

```python
>>> solution(1)
1
>>> solution(3)
4
>>> solution(11)
4
``` 