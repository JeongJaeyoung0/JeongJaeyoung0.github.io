---
layout: post
title: "[Coding test] Programmers_level 1_실패율"
subtitle: "ProgrammersLevel-1-52"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 실패율을 내림차순으로 스테이지 번호 반환

```python
def solution(N, stages):
    fd = {} # 실패 딕셔너리
    per = len(stages) # 전체 플레이어 수
    for i in range(1, N+1): # 1~N 스테이지 for문
        cnt = stages.count(i) # 현재 스테이지의 플레이어 수
        if cnt == 0: # 현재 스테이지에 0명일 경우
            fd[i] = 0 # 실패율 0을 딕셔너리에 담기
        else:
            fr =  cnt / per # 현재 스테이지 플레이어 수 / 전체 플레이어 수
            per -= cnt # 남은 플레이어 수 계산
            fd[i] = fr # 실패율 fr을 딕셔너리에 담기
    return sorted(fd, reverse=True, key=lambda x: fd[x]) # 딕셔너리 value값을 내림차순 하고 key를 반환
```

```python
>>> solution(5, [2, 1, 2, 6, 2, 4, 3, 3])
[3,4,2,1,5]

>>> solution(4, [4,4,4,4,4])
[4,1,2,3]
```