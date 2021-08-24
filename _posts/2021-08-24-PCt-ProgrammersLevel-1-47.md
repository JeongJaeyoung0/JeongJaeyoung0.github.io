---
layout: post
title: "[Coding test] Programmers_level 1_문자열 내림차순으로 배치하기"
subtitle: "ProgrammersLevel-1-47"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/71c03b3290cb1b1a71d1c5540c470294e30d5d54/210824_Programmers_level%201_%E1%84%86%E1%85%AE%E1%86%AB%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%A7%E1%86%AF%20%E1%84%82%E1%85%A2%E1%84%85%E1%85%B5%E1%86%B7%E1%84%8E%E1%85%A1%E1%84%89%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%B3%E1%84%85%E1%85%A9%20%E1%84%87%E1%85%A2%E1%84%8E%E1%85%B5%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5.ipynb)

***

# programmers_level 1_문자열 내림차순으로 배치하기
### 문자를 큰것부터 작은 순으로 정렬하여 반환 (대문자는 소문자보다 작은 것으로 간주)


```python
def solution(s):
    return ''.join(sorted(s, reverse=True)) # 문자 내림차순으로 정렬 후 조인
```


```python
solution("Zbcdefg")
```




    gfedcbZ




```python
solution("ABDCEFvr")
```





    vrFEDCBA
