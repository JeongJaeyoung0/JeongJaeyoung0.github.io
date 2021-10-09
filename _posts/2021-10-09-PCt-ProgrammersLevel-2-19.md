---
layout: post
title: "[Coding test] Programmers_level 2_땅따먹기"
subtitle: "ProgrammersLevel-2-19"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 땅은 총 N행 4열로 이루어져 있고, 모든 칸에는 점수가 쓰여 있으, 각 행의 한 칸만 밟고, 다음 같은 같은 위치를 밟을 수 없을 때, 얻을 수 있는 점수의 최대값을 반환

```python
def solution(land):
    # 첫 번째 땅 점수
    sco = land[0]
    # 두 번째 땅부터 반복문
    for lan in land[1:]:
        # 현재 땅의 1~4번까지, 다음 땅의 1~4까지 중 같은 번호를 제외하였을 때 각 경우별로 최대 값을 sco에 저장(누적으로 점수 저장하는 방식)
        sco = [max([sco[b] + lan[a] for b in range(4) if a != b]) for a in range(4)]
    # 4가지 경우 중 최대값 반환
    return max(sco)
```

```python
>>> solution([[1,2,3,5],[5,6,7,8],[4,3,2,1]])
16
```