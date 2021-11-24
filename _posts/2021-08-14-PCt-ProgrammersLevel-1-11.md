---
layout: post
title: "[Coding test] Programmers_level 1_체육복"
subtitle: "ProgrammersLevel-1-11"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/b7d593bd88be48e7aa8811648f36de795cbf055e/210625_Programmers_level%201_%EC%B2%B4%EC%9C%A1%EB%B3%B5.ipynb)

***

# Programmers_level 1_체육복
### n명의 학생중 lost학생이 체육복을 분실하였고, reserve학생의 옷을 빌려입을(단, 본인번호 +-1 번호만 입을 수 있음) 경우 최대한 많이 체육수업에 참석할 수 있는 인원을 출력


```python
def solution(n, lost, reserve):
    re = set(reserve)       # set화
    lo = set(lost)          # set화
    lost1 = lo - re         # 여분이 없고 잃어버린 학생
    for i in re - lo:       # 잃어버리지 않고 여분을 가진 번호 for문
        f = i - 1           # 여분의 앞번호
        b = i + 1           # 여분의 뒷번호
        if f in lost1:      # 앞번호가 잃어 버렸으면
            lost1.remove(f) # 잃어버린 리스트에서 삭제
        elif b in lost1:    # 뒷번호가 잃어 버렸으면
            lost1.remove(b) # 뒷번호를 리스트에서 삭제
    return n - len(lost1)   # 학생수 - 잃어버린 학생수
```


```python
solution(5, [2, 4], [1, 3, 5])
```




    5




```python
solution(5, [2, 4], [3])
```




    4




```python
solution(3, [3], [1])
```




    2