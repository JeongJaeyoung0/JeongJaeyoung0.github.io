---
layout: post
title: "[Coding test] Programmers_level 2_더 맵게"
subtitle: "ProgrammersLevel-2-07"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 스코빌 지수를 담은 배열이 원하는 지수 이상으로 만들기 위해 섞어야 하는 최소 횟수를 반환

* heapq(힙큐)
    - 이진 트리(binary tree) 기반의 최소 힙(min heap) 자료구조를 제공
    - 기존 리스트 힙으로 변환: heapq.heapify(리스트)
    - 원소 추가: heapq.heappush(리스트, 추가원소)
    - 원소 삭제: heapq.heappop(리스트)
    - 추가 설명: [링크](https://www.daleseo.com/python-heapq/)

```python
import heapq

def solution(scoville, K):
    heap = scoville # heap에 scoville 복제
    heapq.heapify(heap) # 리존 리스트 힙으로 변환
    answer = 0 # 섞는 횟수
    a = heapq.heappop(heap) # 첫 번째 최소값 삭제 및 a에 저장
    while a < K: # 최소값이 K 값보다 적을 경우 while문
        if len(heap) == 0: # 최소값 삭제 후 길이가 0일경우 (k이상 불가능한 경우)
            return -1 # -1 반환
        b = heapq.heappop(heap) # 두 번째 최소값 삭제 및 b에 저장
        heapq.heappush(heap, a + b * 2) # a+b*2를 힙에 추가
        answer += 1 # 섞는 횟수 +1 
        a = heapq.heappop(heap) # 첫 번째 최소값 삭제 및 a에 저장
    return answer # 반환
```

```python
>>> solution([1, 2, 3, 9, 10, 12], 7)
2
```