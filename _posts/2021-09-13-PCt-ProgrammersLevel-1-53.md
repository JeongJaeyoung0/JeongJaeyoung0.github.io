---
layout: post
title: "[Coding test] Programmers_level 1_[1차] 다트 게임"
subtitle: "ProgrammersLevel-1-53"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 다트 게임 점수 계산 로직

```python
def solution(dartResult):
    spl = [n for n, i in enumerate(dartResult) if i.isdigit()] # 숫자 loc 찾기
    spl = [spl[s] for s in range(1, len(spl)) if spl[s-1] != spl[s]-1] # split할 위치 중 첫번째 제외 and 두자리(10) 점수중 첫 숫자 loc만 찾기
    sco = [dartResult[:spl[0]], '+', dartResult[spl[0]:spl[1]], '+', dartResult[spl[1]:]] # 숫자 loc기준 3개 점수를 split하고 그 사이에 '+' 추가
    
    locStar = [] # 스타상(*) 위치 담을 리스트
    for i in range(0, 5, 2): # 점수 위치인 0, 2, 4번째
        if "*" in sco[i]: # 스타상이 있을 경우
            locStar.append(i) # 스타상이 있는 위치 저장
        sco[i] = sco[i].replace("*", "") # '*' 제거
        sco[i] = sco[i].replace("#", "*(-1)") # '#' 치환
        sco[i] = sco[i].replace("S", "**1")  # 'S' 치환
        sco[i] = sco[i].replace("D", "**2") # 'D' 치환
        sco[i] = sco[i].replace("T", "**3") # 'T' 치환
    
    for l in locStar: # 스타상 위치
        sco[l] = sco[l] + "*2" # 그 점수에 스타상 적용
        if l != 0: # 0번째 기회가 아닌 경우
            sco[l-2] = sco[l-2] + "*2" # 전 점수에 스타상 적용
    return eval(''.join(sco)) # 문자열 연산하여 반환
```

```python
>>> solution('1S2D*3T')
37

>>> solution('1D2S#10S')
9

>>> solution('1D2S0T')
3

>>> solution('1S*2T*3S')
23

>>> solution('1D#2S*3S')
5

>>> solution('1T2D3D#')
-4

>>> solution('1D2S3T*')
59

>>> solution('10S10S10S')
30
``` 