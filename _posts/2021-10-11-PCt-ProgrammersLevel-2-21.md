---
layout: post
title: "[Coding test] Programmers_level 2_가장 큰 정사각형 찾기"
subtitle: "ProgrammersLevel-2-21"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 1와 0로 채워진 표(board)가 있고, 표에서 1로 이루어진 가장 큰 정사각형을 찾아 넓이를 반환

```python
def solution(board):
    # 세로 길이
    row = len(board)
    # 가로 길이
    col = len(board[0])
    # 세로 길이만큼 반복문
    for y in range(row):
        # 가로 길이만큼 반복문
        for x in range(col):
            # x 또는 y가 0이 아니면서, 현재 칸의 값이 0이 아닐 경우
            if x * y != 0 and board[y][x] != 0:
                # 현재칸 = (현재칸에서 좌측칸, 윗 칸의 최소값과), 좌측윗칸 중 최소값에서 +1 더한 값
                # 현재칸에서 좌, 위를 방향으로 가장 큰 사각형의 크기값 찾기
                board[y][x] = min(board[y-1][x-1], min(board[y-1][x], board[y][x-1])) + 1
    # board를 한줄씩 반복하여 최대값을 찾고, 그 값의^2 하여 반환
    return max([max(i) for i in board]) ** 2
```

```python
>>> solution([[0,1,1,1],[1,1,1,1],[1,1,1,1],[0,0,1,0]])
9
>>> solution([[0,0,1,1],[1,1,1,1]])
4
```