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

* * *

> ## 아래 코드는 첫 번째 시도였지만, 시간복잡도가 높아서 안됨.
```python
def solution(land):
    answer = 0
    for i in range(len(land)):
        # 첫 for문만 현재 땅 오름차순으로 정렬
        if i == 0:
            dic0 = {num : j for j, num in enumerate(land[i])}
            dic0 = sorted(dic0.items(), reverse=True)
        else:
            dic0.sort(key = lambda x : x[0], reverse=True)
        # for문이 마지막 앞전이 아닐 경우
        if i != len(land)-1:
            # 다음 땅 오름차순 정렬
            dic1 = {num : j for j, num in enumerate(land[i+1])}
            dic1 = sorted(dic1.items(), reverse=True)

            dic0Sco0 = dic0[0][0]
            dic0Sco1 = dic0[1][0]
            dic0Sco2 = dic0[2][0]
            dic0Sco3 = dic0[3][0]
            dic1Sco0 = dic1[0][0]
            dic1Sco1 = dic1[1][0]
            dic1Sco2 = dic1[2][0]
            dic1Sco3 = dic1[3][0]
            # 현재 최고점과 다음 최고점의 인덱스가 같을 경우
            if dic0[0][1] == dic1[0][1]:
                # 첫번째 - 두번째 점수가 현재가 더 큰 경우
                if dic0Sco0 - dic0Sco1 > dic1Sco0 - dic1Sco1:
                    answer += dic0Sco0
                    n = dic0[0][1]
                    for k in range(4):
                        if dic1[k][1] == n:
                            change = list(dic1[k])
                            change[0] = 0
                            dic1[k] = change
                    dic0 = dic1
                    continue
                # 첫번째 - 두번째 점수가 다음이 더 큰 경우
                elif dic0Sco0 - dic0Sco1 < dic1Sco0 - dic1Sco1:
                    answer += dic0Sco1
                    n = dic0[1][1]
                    for k in range(4):
                        if dic1[k][1] == n:
                            change = list(dic1[k])
                            change[0] = 0
                            dic1[k] = change
                    dic0 = dic1
                    continue
                # 첫번째 - 두번째 점수가 같을 경우
                else:
                    # 현 점수가 크거나 같을 경우
                    if dic0Sco0 >= dic1Sco0:
                        answer += dic0Sco0
                        n = dic0[0][1]
                        for k in range(4):
                            if dic1[k][1] == n:
                                change = list(dic1[k])
                                change[0] = 0
                                dic1[k] = change
                        dic0 = dic1
                        continue
                    # 다음 점수가 클 경우
                    else:
                        answer += dic0Sco1
                        n = dic0[1][1]
                        for k in range(4):
                            if dic1[k][1] == n:
                                change = list(dic1[k])
                                change[0] = 0
                                dic1[k] = change
                        dic0 = dic1
                        continue
            # 인덱스가 다를 경우
            else:
                answer += dic0Sco0
                n = dic0[0][1]
                for k in range(4):
                    if dic1[k][1] == n:
                        change = list(dic1[k])
                        change[0] = 0
                        dic1[k] = change
                dic0 = dic1
        # 마지막 땅일 경우
        else:
            answer += dic0[0][0]
    return answer
```