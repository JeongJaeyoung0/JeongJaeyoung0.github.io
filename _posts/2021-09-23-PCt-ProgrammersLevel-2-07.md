---
layout: post
title: "[Coding test] Programmers_level 2_더 맵게"
subtitle: "ProgrammersLevel-2-07"
categories: python
tags: codingtest
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
    heap = scoville
    heapq.heapify(heap)
    answer = 0
    a = heapq.heappop(heap)
    while a < K:
        if len(heap) == 0:
            return -1
        b = heapq.heappop(heap)
        heapq.heappush(heap, a + b * 2)
        answer = answer + 1
        a = heapq.heappop(heap)
    return answer
```

```python
>>> solution([1, 2, 3, 9, 10, 12], 7)
2
```