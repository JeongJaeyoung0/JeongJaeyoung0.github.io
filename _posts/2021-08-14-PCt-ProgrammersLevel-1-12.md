---
layout: post
title: "[Coding test] Programmers_level 1_완주하지 못한 선수"
subtitle: "ProgrammersLevel-1-12"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210626_Programmers_level%201_%EC%99%84%EC%A3%BC%ED%95%98%EC%A7%80%20%EB%AA%BB%ED%95%9C%20%EC%84%A0%EC%88%98.ipynb)

***

# Programmers_level 1_완주하지 못한 선수
### 선수 중 완주하지 못한 선수가 단 1명 있는데, 그 선수의 이름을 출력


```python
import collections

def solution(participant, completion):
    answer = collections.Counter(participant) - collections.Counter(completion) # 완주한선수 - 전체선수 Counter해서 빼기
    return list(answer.keys())[0]   # 완주하지 못한 선수 keys값을 출력
```


```python
solution(["leo", "kiki", "eden"], ["eden", "kiki"])
```




    'leo'




```python
solution(["marina", "josipa", "nikola", "vinko", "filipa"], ["josipa", "filipa", "marina", "nikola"])
```




    'vinko'




```python
solution(["mislav", "stanko", "mislav", "ana"], ["stanko", "ana", "mislav"])
```




    'mislav'