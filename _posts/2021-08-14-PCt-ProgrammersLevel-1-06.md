---
layout: post
title: "[Coding test] Programmers_level 1_소수 만들기"
subtitle: "ProgrammersLevel-1-6"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/47260434954f847c235852888aa8942a186319c0/210620_Programmers_level%201_%EC%86%8C%EC%88%98%20%EB%A7%8C%EB%93%A4%EA%B8%B0.ipynb)

***

# Programmers_level 1_소수 만들기
### 주어진 숫자 중 3개를 더했을 때 소수가 되는 경우의 수 출력


```python
# 에라토스테네스 체 이용하여 판별
import math
n=2997                                      # 조건에서 가장 높은 수의 경우
t=[True for i in range(n+1)]                # n자리 수에 모두 True로 리스트 만들기
for i in range(2,int(math.sqrt(n))+1):      # 에라토스테네스의 체 (소수를 찾는 방법) / n까지의 제곱근을 for문
    if t[i]==True:                          # 그 자리가 True일 경우
        a=2                                 # 그 자리수의 배수
        while i*a<=n:
            t[i*a]=False                    # 전부다 False로 처리(False=소수가 아닌 수)
            a+=1
prime_number = [i for i in range(2,n+1) if t[i]]    # True인(소수인) 수를 리스트로 저장

def solution(nums):
    n=len(nums)                             # 입력받은 수의 개수
    return sum([nums[i]+nums[j]+nums[k] in prime_number for i in range(n) for j in range(i+1,n-1) for k in range(j+1,n)]) # 중복되지 않고 3개의 수로 조합 가능한 경우를 찾고 sum하여 그 수가 prime_number(소수)에 있을 경우 카운트
```


```python
# 해당 수마다 소수인지 판별
from itertools import combinations as cb

def solution(nums):
    answer=0
    for i in cb(nums, 3):           # 중복되지 않는 3개의 수를 for문
        for j in range(2, sum(i)):  # 2부터 3개의 수의 합까지 for문
            if sum(i)%j==0:         # 합을 2부터 본인 수를 제외한 모든 수를 나누고, 나머지가 0일 경우
                break               # break(현재 수는 소수가 아님)
        else: answer+=1             # for문과 같은 줄에 else를 사용할 경우, for문이 끝나고 실행
    return answer
```


```python
solution([1,2,3,4])
```




    1




```python
solution([1,2,7,6,4])
```




    4