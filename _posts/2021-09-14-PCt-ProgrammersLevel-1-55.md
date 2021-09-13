---
layout: post
title: "[Coding test] Programmers_level 1_없는 숫자 더하기"
subtitle: "ProgrammersLevel-1-55"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 5개의 직업군 별로 언어 선호도가 가장 높은 직업군을 리턴 (선호도 점수가 같을 경우 직업군 사전 순으로 가장 빠른 직업굴을 리턴)

```python
def solution(table, languages, preference):
    tabRever = [list(reversed(t.split(' '))) for t in table] # table를 split하여 역순으로 리스트
    
    totalSco = {} # 총합 점수를 담을 딕셔너리
    for tr in tabRever:
        sum = 0 # 합계 점수 리셋
        for i in range(len(languages)): # languages의 개수만큼 for문
            try:
                sco = (tr.index(languages[i])+1) * preference[i] # table에 languages의 위치를 찾고 +1 값을 preference와 곱
            except:
                continue # table에 languages이 없을 경우 다음 for문 진행
            sum += sco # 총합
        totalSco[tr[-1]] = sum # 딕셔처리 키에 총합 저장

    return sorted([key for key, value in totalSco.items() if value == max(totalSco.values())])[0] # 딕셔너리 value중 최대값의 key를 리스트로 저장하고, 오름차순 정렬 후 첫번째 key를 리턴
```

```python
>>> solution(["SI JAVA JAVASCRIPT SQL PYTHON C#", "CONTENTS JAVASCRIPT JAVA PYTHON SQL C++", "HARDWARE C C++ PYTHON JAVA JAVASCRIPT", "PORTAL JAVA JAVASCRIPT PYTHON KOTLIN PHP", "GAME C++ C# JAVASCRIPT C JAVA"], ["PYTHON", "C++", "SQL"], [7, 5, 5])
"HARDWARE"

>>> solution(["SI JAVA JAVASCRIPT SQL PYTHON C#", "CONTENTS JAVASCRIPT JAVA PYTHON SQL C++", "HARDWARE C C++ PYTHON JAVA JAVASCRIPT", "PORTAL JAVA JAVASCRIPT PYTHON KOTLIN PHP", "GAME C++ C# JAVASCRIPT C JAVA"], ["JAVA", "JAVASCRIPT"], [7, 5])
"PORTAL"
``` 