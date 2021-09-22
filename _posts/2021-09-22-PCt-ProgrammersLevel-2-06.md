---
layout: post
title: "[Coding test] Programmers_level 2_기능개발"
subtitle: "ProgrammersLevel-2-06"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 작업 진도, 속도가 주어졌을 때, 배포마다 몇 개의 기능이 배포되는지 반환

```python
def solution(progresses, speeds):
    answer = [] # 반환할 리스트
    function = 1 # 배포되는 기능 개수
    previous = 0 # 앞전 배포 작업 일수
    for p, s in zip(progresses, speeds): # zip함수로 리스트 요소 하나씩 for문
        q = -((p-100)//s) # p/s 에서 나머지값 올림 (ceil 함수 사용하지 않고 음수 이용함)
        if previous == 0: # 첫 번째 for문 검출
            previous = q # 앞전 작업 일수에 현재 작업 일수
            continue # 첫 번째 for문 종료
        if previous >= q: # 앞전 작업 일수가 현재보다 클 경우
            function += 1 # 기능 개수 1개 추가
        else: # 앞전 작업 일수보다 작은 경우
            answer.append(function) # 기능 개수를 반환할 리스트에 추가
            previous = q # 앞전 작업 일수는 현재 작업 일수
            function = 1 # 배포되는 기능 개수 1개로 초기화
    answer.append(function) # 마지막 기능 개수를 반환할 리스트에 추가
    return answer
```

```python
>>> solution([93, 30, 55], [1, 30, 5])
[2, 1]
>>> solution([95, 90, 99, 99, 80, 99], [1, 1, 1, 1, 1, 1])
[1, 3, 2]
```