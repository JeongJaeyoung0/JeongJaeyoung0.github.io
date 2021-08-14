---
layout: post
title: "[Coding test] Programmers_level 1_모의고사"
subtitle: "ProgrammersLevel-1-13"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210627_Programmers_level%201_%EB%AA%A8%EC%9D%98%EA%B3%A0%EC%82%AC.ipynb)

***

# Programmers_level 1_모의고사
### 1번 수포자 찍는 방식 : 1, 2, 3, 4, 5, 1, 2, 3, 4, 5 ...
### 2번 수포자 찍는 방식 : 2, 1, 2, 3, 2, 4, 2, 5 ...
### 3번 수포자 찍는 방식 : 3, 3, 1, 1, 2, 2, 4, 4, 5, 5 ...


```python
def solution(answers):
    pat1 = [1,2,3,4,5]
    pat2 = [2,1,2,3,2,4,2,5]
    pat3 = [3,3,1,1,2,2,4,4,5,5]
    score = [0, 0, 0]
    for i, j in enumerate(answers):         # enumerate 함수로 index, list로 for문
        score[0] += j == pat1[i%len(pat1)]  # 정답과 pat1의 답과 같으면 +1
        score[1] += j == pat2[i%len(pat2)]  # 정답과 pat2의 답과 같으면 +1
        score[2] += j == pat3[i%len(pat3)]  # 정답과 pat3의 답과 같으면 +1
    answer = [i+1 for i, j in enumerate(score) if j == max(score)]  # score중 최고 점수와 비교하여 최다점 번호 리스트
    return answer                           # 최다 점수자 return
```


```python
solution([1,2,3,4,5])
```




    [1]




```python
solution([1,3,2,4,2])
```




    [1, 2, 3]