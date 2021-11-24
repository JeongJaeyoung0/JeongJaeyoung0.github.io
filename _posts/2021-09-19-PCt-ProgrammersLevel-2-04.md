---
layout: post
title: "[Coding test] Programmers_level 2_멀쩡한 사각형"
subtitle: "ProgrammersLevel-2-04"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 격자가 그러진 직사각형을 대각선 방향으로 잘랐을 경우 사용 할 수 있는 격자의 갯수를 반환

```python
# 첫 번째 풀이
def solution(w,h):
    if w == 1 or h == 1: # 가로 또는 세로가 1칸일 경우
        return 0 # 모든 격자를 사용하지 못함
    elif w == h: # 가로와 세로가 같은 정사각형의 경우
        return w * h - w # 전체 개수에서 한변의 길이만큼 사용하지 못함
    else: # 직사각형일 경우
        return sum([int(h - h / w * i) for i in range(1, w+1)]) * 2 # 좌 → 우 칸마다 기울기 값만큼 빼주고 정수화 하여 전체를 합하여 리턴
```

```python
# 두 번째 풀이
def gcd(a,b): return b if (a==0) else gcd(b%a,a) # 최대 공약수 계산
def solution(w,h): return w*h-w-h+gcd(w,h) # 가로 * 세로 - 가로 - 세로 + 최대 공약수
# 사용하지 못하는 격자는 가로 + 세로에서 공통이되는 최대 공약수를 제외
```

```python
>>> solution(8, 12)
80
```