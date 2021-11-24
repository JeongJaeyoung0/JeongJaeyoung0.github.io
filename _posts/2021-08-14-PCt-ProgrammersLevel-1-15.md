---
layout: post
title: "[Coding test] Programmers_level 1_예산"
subtitle: "ProgrammersLevel-1-15"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/0ee93217f78f849aa2a9b8dd684e7edc7628c58a/210629_Programmers_level%201_%EC%98%88%EC%82%B0.ipynb)

***

# Programmers_level 1_예산
### d는 부서별로 신청한 금액, budget은 예산일 경우 최대 지원해 줄 수 있는 부서의 수를 출력


```python
def solution(d, budget):
    d.sort()                    # 신청액 정렬
    sum = 0                     # 신청액 합계
    for i, j in enumerate(d):   # 신청액 하나씩 for문
        sum += j                # 신청액 하나씩 합
        if sum > budget:        # 신청액이 예산을 초과하면
            answer = i          # i번째를 return
            break               # for문 종료
        else:                   # 예산을 초과하지 않으면(모든 부서 지원가능)
            answer = i+1        # i+1번재를 return
    return answer
```


```python
solution([1,3,2,5,4], 9)
```




    3




```python
solution([2,2,3,3], 10)
```




    4