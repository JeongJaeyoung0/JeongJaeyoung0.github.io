---
layout: post
title: "[Coding test] Programmers_level 2_문자열 압축"
subtitle: "ProgrammersLevel-2-02"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 문자열s를 1개 이상 단위로 잘라 압축하였을 경우 가장 짧은 것의 길이를 반환

```python
def solution(s):
    answer = [] # 길이 담을 리스트
    for i in range(1, len(s)//2+2): # 전체 길이만큼 돌면 시간 낭비이기 때문에 절반+1 까지만 for문
        l=i # 초기 문자 길이는 자를 단위(i) 값
        overlap = 1 # 문자가 반복되는 횟수 초기화
        for j in range(0, len(s), i): # 문자 전체 길이를 자를 단위(i)만큼 띄워서 for문
            if j != 0: # 첫번째 문자가 아닌 경우
                text = s[j:j+i] # 현재 입력되는 문자
                if text == s[j-i:j]: # 현재 문자와 이전 문자가 같은 경우
                    overlap += 1 # 반복 횟수 +1
                    if text == s[j-i*2:j-i]: # 이전 전 문자와 같은 경우는 continue
                        if overlap == 10: # 단, 10번째 반복 될 경우 문자 길이 +1
                            l += 1
                        continue
                    else: # 이전 문자와 같으면 길이 +1
                        l += 1
                else: # 이전 문자와 같지 않는 경우
                    l += len(text) # 다음 문자의 길이 +
                    overlap = 1 # 문자가 반복되는 횟수 초기화
        answer.append(l) # 전체 문자 길이 리스트에 추가
    return min(answer) # 리스트에서 최소값 반환
```

```python
>>> solution("aabbaccc")
7
>>> solution("ababcdcdababcdcd")
9
>>> solution("abcabcabcabcdededededede")
14
``` 