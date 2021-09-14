---
layout: post
title: "[Coding test] Programmers_level 1_복서 정렬하기"
subtitle: "ProgrammersLevel-1-56"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 승률 높은 순 > 무게가 높은 복서 이긴 횟수 많은 순 > 몸무게 무거운 순 > 복서 번호 낮은 순

```python
def solution(weights, head2head):
    boxer = [] # 계산 결과 담을 리스트
    n = len(weights) # 복서 수
    for i in range(n): # 복서 수 만큼 for문 (본인)
        matche = 0 # 경기 횟수
        win = 0 # 이긴 횟수
        heavy = 0 # 본인보다 무게가 높은 복서 이긴 횟수
        for j in range(n): # 복서 수 만큼 for문 (상대)
            if not i == j and head2head[i][j] != 'N': # 본인이 아니면서, 'N'이 아닌(붙은적이 있는) 경우
                matche += 1 # 경기 횟수 +1
                if head2head[i][j] == 'W': # 이겼을 경우
                    win += 1 # 이긴 횟수 +1
                    if weights[i] < weights[j]: # 상대보다 몸무게가 가벼운 경우
                        heavy += 1 # 무게가 높은 복서 이긴 횟수 +1
        if matche == 0: # 경기한 적이 없는 경우
            winRate = 0 # 승률 0
        else:
            winRate = win / matche # 승률 계산
        boxer.append({'num': i+1, 'winRate': winRate, 'heavy': heavy, 'weight': weights[i]}) # 리스트에 딕셔너리 형태로 추가
    sorted_dict = sorted(boxer, key = lambda x : (-x['winRate'], -x['heavy'], -x['weight'], x['num'])) # 'winRate' 내림차순, 'heavy' 내림차순, 'weight' 내림차순, 'num' 오름차순 으로 정렬
    return [k['num'] for k in sorted_dict] # 정렬된 리스트에서 num만 리스트로 반환
```

```python
>>> solution([50,82,75,120], ["NLWL","WNLL","LWNW","WWLN"])
[3,4,1,2]

>>> solution([145,92,86], ["NLW","WNL","LWN"])
[2,3,1]

>>> solution([60,70,60], ["NNN","NNN","NNN"])
[2,1,3]
``` 