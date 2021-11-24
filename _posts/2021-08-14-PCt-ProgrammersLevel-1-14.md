---
layout: post
title: "[Coding test] Programmers_level 1_3진법 뒤집기"
subtitle: "ProgrammersLevel-1-14"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210628_Programmers_level%201_3%EC%A7%84%EB%B2%95%20%EB%92%A4%EC%A7%91%EA%B8%B0.ipynb)

***

# Programmers_level 1_3진법 뒤집기
### n을 3진법 상에서 앞뒤로 뒤집은 후 다시 10진법으로 출력


```python
# divmod 내장 함수 이용 방법
def solution(n):
    answer = ''
    while n:                    # n=0일 경우 False가 되기 때문에 while문 종료
        n, rest = divmod(n, 3)  # 몫과 나머지를 반환해주는 함수
        answer += str(rest)     # 나머지를 문자열로 추가
    answer = int(answer, 3)     # int(x, 3) : x값이 3진법일 때 10진법으로 변환
    return answer
```


```python
# 연산 이용 방법
def solution(n):
    answer = ''
    while n:
        answer += str(n % 3)
        n = n // 3
    answer = int(answer, 3)
    return answer
```


```python
solution(45)
```




    7




```python
solution(125)
```




    229