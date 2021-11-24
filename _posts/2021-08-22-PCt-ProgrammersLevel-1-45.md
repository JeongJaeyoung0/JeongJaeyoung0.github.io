---
layout: post
title: "[Coding test] Programmers_level 1_서울에서 김서방 찾기"
subtitle: "ProgrammersLevel-1-45"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/30a106298e0c4c67d17af704313921bf9e658805/210822_Programmers_level%201_%E1%84%89%E1%85%A5%E1%84%8B%E1%85%AE%E1%86%AF%E1%84%8B%E1%85%A6%E1%84%89%E1%85%A5%20%E1%84%80%E1%85%B5%E1%86%B7%E1%84%89%E1%85%A5%E1%84%87%E1%85%A1%E1%86%BC%20%E1%84%8E%E1%85%A1%E1%86%BD%E1%84%80%E1%85%B5.ipynb)

***

# programmers_level 1_서울에서 김서방 찾기
### 문자열 seoul의 요소 중 "Kim"의 위치 x를 찾아, "김서방은 x에 있다"는 문자열을 반환 ("Kim"은 오직 한번만 나타나며 잘못된 값은 없음")


```python
def solution(seoul):
    return "김서방은 %i에 있다" %(seoul.index("Kim"))
```


```python
solution(["Jane", "Kim"])
```




    김서방은 1에 있다
