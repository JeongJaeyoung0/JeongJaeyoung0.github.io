---
layout: post
title: "[Coding test] Programmers_level 2_프린터"
subtitle: "ProgrammersLevel-2-24"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 현재 대기목록에 있는 문서의 중요도가 순서대로 담긴 배열 priorities와 내가 인쇄를 요청한 문서가 현재 대기목록의 어떤 위치에 있는지를 알려주는 location이 매개변수로 주어질 때, 내가 인쇄를 요청한 문서가 몇 번째로 인쇄되는지 반환

```python
def solution(priorities, location):
    # (중요도, 초기 순번)
    arr = [(p, n) for n, p in enumerate(priorities)]
    # 중요도 높은 순서로 정렬
    priorities.sort(reverse=True)
    # 목록 개수만큼 반복문
    for i in range(len(priorities)):
        # 대기목록의 index 와 중요도의 index를 비교하여 반복문
        while arr[i][0] != priorities[i]:
            # 다를 경우 index의 순번을 제거하고 추가 (잴 뒤로 보내기)
            arr.append(arr.pop(i))
    # 프린트 순서대로 정렬한 것을 반복문
    for i, a in enumerate(arr):
        # 내가 요청한 문서의 위치를 찾아서
        if a[1] == location:
            # +1 하여 반환
            return i + 1
```

```python
>>> solution([2, 1, 3, 2], 2)
1
>>> solution([1, 1, 9, 1, 1, 1], 0)
5
```