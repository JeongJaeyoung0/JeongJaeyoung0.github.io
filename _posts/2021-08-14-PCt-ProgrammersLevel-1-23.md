---
layout: post
title: "[Coding test] Programmers_level 1_문자열 내 마음대로 정렬하기"
subtitle: "ProgrammersLevel-1-23"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/c4bbd2fc33927238b431e05e752aa9e8b474b1c3/210707_Programmers_level%201_%EB%AC%B8%EC%9E%90%EC%97%B4%20%EB%82%B4%20%EB%A7%88%EC%9D%8C%EB%8C%80%EB%A1%9C%20%EC%A0%95%EB%A0%AC%ED%95%98%EA%B8%B0.ipynb)

***

# Programmers_level 1_문자열 내 마음대로 정렬하기
### 문자열 strings와 정수 n일 경우, 문자열의 인덱스 n번째 글자를 기준으로 오름차순 정렬하여 반환


```python
def solution(strings, n):
    return sorted(sorted(strings), key=lambda x: x[n])  # 정렬을 먼저 하고, n번째 key를 기준으로 다시 한번더 정렬후 반환
```


```python
solution(["sun", "bed", "car"], 1)
```




    ['car', 'bed', 'sun']




```python
solution(["abce", "abcd", "cdx"], 2)
```




    ['abcd', 'abce', 'cdx']