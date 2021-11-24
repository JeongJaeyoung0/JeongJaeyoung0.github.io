---
layout: post
title: "[Coding test] Programmers_level 1_이상한 문자 만들기"
subtitle: "ProgrammersLevel-1"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/0bc4f65cedf347fd2a26fcd40ffbd5994e5f112a/210615_Programmers_level%201_%EC%9D%B4%EC%83%81%ED%95%9C%20%EB%AC%B8%EC%9E%90%20%EB%A7%8C%EB%93%A4%EA%B8%B0.ipynb)

***

# Programmers_level 1_이상한 문자 만들기
### 단어별 짝수자리: 대문자, 홀수자리: 소문자


```python
# 풀어 쓴 형태
def solution(s):
    a = s.split(' ')        # 단어별 끊기
    text=[]                 # text 담을 list
    for x in range(len(a)): # 단어 수 만큼 for문
        text1 = []          # text1 담을 list
        for y in range(len(a[x])):                                  # 각 단어의 길이만큼 for문
            text1.append([a[x][y].upper(),a[x][y].lower()][y%2])    # y%2 = 홀, 짝수 구분 / 홀수는 대문자, 짝수는 소문자로 변환 후 text1에 담기
        text.append(''.join(text1)) # text1 list를 하나로 이어붙여 text에 담기
    answer = ' '.join(text)         # text list를 하나로 이어붙여 answer로 담기
    return answer                   # answer return
```


```python
# short coding
def solution(s):
    a = s.split(' ')
    return ' '.join(list(map(lambda x:''.join(list(map(lambda y:[a[x][y].upper(),a[x][y].lower()][y%2],range(len(a[x]))))),range(len(a)))))
```


```python
solution("try hello world")
```




    'TrY HeLlO WoRlD'