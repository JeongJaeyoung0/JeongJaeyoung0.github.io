---
layout: post
title: "[Coding test] Programmers_level 2_행렬 테두리 회전하기"
subtitle: "ProgrammersLevel-2-09"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : rows * columns 행렬의 숫자, 회전들의 목록 queries가 주어질 때, 각 회전들을 배열에 적용한 뒤, 그 회전에 의해 위치가 바뀐 숫자들 중 가장 작은 숫자들을 순서대로 반환

```python
def solution(rows, columns, queries):
    answer = [] # 결과 반환할 리스트
    matrix = list(range(1,rows*columns+1)) # 행렬 리스트로 만들기

    for i in range(len(queries)):
        rcol = queries[i][3] - queries[i][1] + 1 # 우측 회전 크기
        lcol = rcol # 좌측 회전 크기
        brow = queries[i][2] - queries[i][0] + 1 # 하단 회전 크기
        trow = brow # 상단 회전 크기

        location = [] # 회전할 위치 담을 리스트
        location.append((queries[i][0] - 1) * columns + queries[i][1]) # 회전 시작되는 위치 (좌상단)
        while rcol > 1: # 시작에서 우측 회전 위치
            location.append(location[-1] + 1)
            rcol -= 1
        while brow > 1: # 우상단에서 하단으로 회전 위치
            location.append(location[-1] + columns)
            brow -= 1
        while lcol > 1: # 우하단에서 좌측으로 회전 위치
            location.append(location[-1] - 1)
            lcol -= 1
        while trow > 2: # 좌하단에서 상단으로 회전 위치 (시작점 제외)
            location.append(location[-1] - columns)
            trow -= 1

        rotation = [matrix[j-1] for j in location] # 회전할 숫자 리스트
        rotation.insert(0, rotation.pop()) # 회전할 리스트 중 가장 끝 수를 제거하고 첫 번째에 추가
        for l, r in zip(location, rotation): # 회전할 위치와 회전된 수를 for문
            matrix[l-1] = r # 회전할 위치 = 회전된 수
        answer.append(min(rotation)) # 회전할 수 중 가장 작은 수 추가
    return answer
```

```python
>>> solution('baabaa')
1
>>> solution('cdcd')
0
```