---
layout: post
title: "[Coding test] Programmers_level 2_카펫"
subtitle: "ProgrammersLevel-2-28"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 카펫 테두리 1줄을 갈색, 내부는 노란색이며 갈색 격자수, 노란색 격자수를 변수로 주어졌을 때, 카펫의 가로, 세로의 크기를 배열로 반환

```python
def solution(brown, yellow):
    # 노란색 카펫의 가능한 (가로, 세로) 배열
    y = [(yellow // y, y) for y in range(1, int(yellow ** 0.5) + 1) if yellow % y == 0]
    # 배열 for문
    for x, y in y:
        # 배열 중 갈색의 개수의 경우가 가능 할 경우
        if brown == (x + y) * 2 + 4:
            # 노란색 배열 + 2만큼 반환
            return [x + 2, y + 2]
```

```python
>>> solution(10, 2)
[4, 3]

>>> solution(8, 1)
[3, 3]

>>> solution(24, 24)
[8, 6]
```