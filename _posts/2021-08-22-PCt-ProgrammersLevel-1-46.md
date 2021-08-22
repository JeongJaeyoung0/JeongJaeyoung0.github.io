---
layout: post
title: "[Coding test] Programmers_level 1_신규 아이디 추천"
subtitle: "ProgrammersLevel-1-46"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/a017448dc2e77526f1ad5c2f5c8ce32a886f21d2/210822_Programmers_level%201_%E1%84%89%E1%85%B5%E1%86%AB%E1%84%80%E1%85%B2%20%E1%84%8B%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B5%20%E1%84%8E%E1%85%AE%E1%84%8E%E1%85%A5%E1%86%AB.ipynb)

***

# programmers_level 1_신규 아이디 추천
### 신규 유저가 규칙에 맞지 않는 아이디를 입력할 경우 유사하면서 규칙에 맞는 추천 아이디를 반환
### 규칙: 아이디 길이: 3~15 / 알파벳 소문자, 숫자, 빼기, 밑줄, 마침표만 사용 가능 / 단 마침표는 처음과 끝에 사용할 수 없으며 또한 연속 사용 불가


```python
def solution(new_id):
    import re
    # 1단계. 모든 대문자를 소문자로 치환
    id = new_id.lower()
    # 2단계. 아파벳 소문자, 숫자, -, _, .,를 제외한 모든 문자 제거
    id = re.sub(r"[^a-zA-Z0-9-_.]","",id)
    # 3단계. .가 2번 이상 연속된 부분을 하나의 .로 치환
    if len(id) > 0:
        i = 1
        while i < len(id):
            if id[i] == '.' and id[i-1] == '.':
                id = id[:i-1] + id[i:]
                i -= 1
            i += 1
        # 4단계. .가 처음이나 끝에 위치하면 제거
        if id[0] == '.':
            id = id[1:]
        if len(id) != 0 and id[-1] == '.':
            id = id[:-1]
    # 5단계. 빈 문자열이면 a를 대입
    if id == '':
        id = 'a'
    # 6단계. 길이가 16자 이상이면, 첫 15개의 문자를 제외한 나머지 문자 제거. 제거 후 .가 끝에 위치하면 .도 제거
    if len(id) > 15:
        id = id[:15]
    if id[-1] == '.':
        id = id[:-1]
    # 7단계. 길이가 2자 이하일 경우 마지막 문자를 길이가 3이 될 때까지 반복
    while len(id) < 3:
        id = id + id[-1]
    return id
```


```python
solution("...!@BaT#*..y.abcdefghijklm")
```




    bat.y.abcdefghi




```python
solution("z-+.^.")
```





    z--




```python
solution("=.=")
```





    aaa




```python
solution("123_.def")
```





    123_.def




```python
solution("abcdefghijklmn.p")
```





    abcdefghijklmn