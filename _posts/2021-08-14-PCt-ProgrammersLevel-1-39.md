---
layout: post
title: "[Coding test] Programmers_level 1_문자열을 정수로 바꾸기"
subtitle: "ProgrammersLevel-1-2"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/5a6864d0c7a401755624bb0faba5cca15623035e/210726_Programmers_level%201_%EB%AC%B8%EC%9E%90%EC%97%B4%EC%9D%84%20%EC%A0%95%EC%88%98%EB%A1%9C%20%EB%B0%94%EA%BE%B8%EA%B8%B0.ipynb)

***

# Programmers_level 1_시저 암호
### s의 값을 n만큼 시저 암호화 하여 반환 (시저 암호: 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식)


```python
# 새로운 리스트 만드는 방법
def solution(s, n):
    answer = []
    for i in s:
        if ord(i) == ord(" "):                                  # 공백일 경우
            answer.append(" ")
        elif ord("A") <= ord(i) <= ord("Z"):                    # 대문자일 경우
            answer.append(chr((ord(i)-ord("A")+n)%26+ord("A")))
        elif ord("a") <= ord(i) <= ord("z"):                    # 소문자일 경우
            answer.append(chr((ord(i)-ord("a")+n)%26+ord("a")))
    return ''.join(answer)  # ord: 문자를 아스키 코드로 / chr: 아스키 코드를 문자로
```


```python
# 기존 리스트를 수정하는 방법
def solution(s, n):
    s = list(s)
    for i in range(len(s)):
        if s[i].isupper():                                  # 대문자일 경우
            s[i]=chr((ord(s[i])-ord('A')+ n)%26+ord('A'))
        elif s[i].islower():                                # 소문자일 경우
            s[i]=chr((ord(s[i])-ord('a')+ n)%26+ord('a'))
    return ''.join(s)
```


```python
solution("AB", 1)
```




    'BC'




```python
solution("z", 1)
```




    'a'




```python
solution("a B z", 4)
```




    'e F d'