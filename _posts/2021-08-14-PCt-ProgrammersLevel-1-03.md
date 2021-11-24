---
layout: post
title: "[Coding test] Programmers_level 1_1차 비밀지도"
subtitle: "ProgrammersLevel-1-3"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/9f41ee5cb6c3bd1aad2ba931f36e8edfefe8c460/210617_Programmers_level%201_1%EC%B0%A8%20%EB%B9%84%EB%B0%80%EC%A7%80%EB%8F%84.ipynb)

***

# Programmers_level 1_1차 비밀지도
### 2개의 지도를 2진수로 받고, NOR 게이트로 출력


```python
def solution(n, arr1, arr2):
    answer = []                                 # 정답 지도 리스트
    map1 = [bin(i)[2:].zfill(n) for i in arr1]  # 첫 번째 지도 row별 2진수 변환 후 리스트 저장
    map2 = [bin(i)[2:].zfill(n) for i in arr2]  # 두 번째 지도 row별 2진수 변환 후 리스트 저장
    for i in range(n):                          # n행만큼 for문
        answer += [''.join(([' ' if m1+m2=='00' else '#' for m1, m2 in zip(map1[i], map2[i])]))]    # 각 맵의 row별로 둘다 0일 경우는 빈캄, 하나라도 0이 아닐 경우 #으로 반환 후 리스트 저장
    return answer                               # 정답 리턴
```


```python
solution(5, [9, 20, 28, 18, 11], [30, 1, 21, 17, 28])
```




    ['#####', '# # #', '### #', '#  ##', '#####']


