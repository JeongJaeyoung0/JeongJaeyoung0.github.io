---
layout: post
title: "[Coding test] Programmers_level 2_메뉴 리뉴얼"
subtitle: "ProgrammersLevel-2-10"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 단품메뉴 배열 orders, 코스요리를 구성하는 단품메뉴들의 갯수가 담긴 배열 course, 새로 추가하게 될 코스요리의 메뉴 구성을 문자열 형태로 배열에 담아 반환

```python
from itertools import combinations

def solution(orders, course):
    courseMenuList = [] # 조합 가능한 코스메뉴 리스트 담을 리스트
    for i in course:
        combi = [list(combinations(sorted(j), i)) for j in orders] # i개로 구성 가능한 메뉴를 오름차순정렬하여 리스트로 저장
        courseMenuList.append([''.join(k) for k in sum(combi, [])]) # 리스트내 리스트의 문자열을 join하여 저장

    answer = [] # 결과를 저장할 리스트
    for a in range(len(courseMenuList)):
        menuCnt = {} # 메뉴별 카운트 할 딕셔너리
        for b in set(courseMenuList[a]): # 중복을 제외하고 for문
            cnt = courseMenuList[a].count(b) # 조합한 메뉴가 들어있는 개수 카운트
            if cnt > 1: # 메뉴가 1개 초과일 경우
                menuCnt[b] = cnt # 메뉴이름을 key, 카운트 수를 values로 저장
        if len(menuCnt) != 0: # 수량이 존재할 경우
            maxValues = max(menuCnt.values()) # 최대값 찾기
            answer.append([k for k, v in menuCnt.items() if v == maxValues]) # 딕셔너리에 값이 최대값과 같은 key를 answer에 추가

    return sorted(sum(answer, [])) # 오룸차순으로 정렬하려 반환
```

```python
>>> solution(["ABCFG", "AC", "CDE", "ACDE", "BCFG", "ACDEH"], [2, 3, 4])
["AC", "ACDE", "BCFG", "CDE"]

>>> solution(["ABCDE", "AB", "CD", "ADE", "XYZ", "XYZ", "ACD"], [2, 3, 5])
["ACD", "AD", "ADE", "CD", "XYZ"]

>>> solution(["XYZ", "XWY", "WXA"], [2, 3, 4])
["WX", "XY"]
```
