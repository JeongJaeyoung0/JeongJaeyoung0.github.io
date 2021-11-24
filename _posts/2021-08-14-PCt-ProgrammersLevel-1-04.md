---
layout: post
title: "[Coding test] Programmers_level 1_키패드 누르기"
subtitle: "ProgrammersLevel-1-4"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/1432f26fb2c8a1e6c3a52962dbde0883a01a66b5/210618_Programmers_level%201_%ED%82%A4%ED%8C%A8%EB%93%9C%20%EB%88%84%EB%A5%B4%EA%B8%B0.ipynb)

***

# Programmers_level 1_키패드 누르기
### 1,4,7은 왼손 / 3, 6, 9는 오른손 / 가운데 버튼은 현재 엄지손가락에서 가까운 손가락으로 누를 경우 키패드를 누르는 왼/오를 순차적으로 출력


```python
def solution(numbers, hand):
    answer = ''
    l_hand ,r_hand = 10, 12     # 왼손, 오른손 시작 위치
    for i in numbers:           # 키패드 누를 값 for문
        if i in [1, 4, 7]:      # 1, 4, 7은 왼손
            answer += "L"
            l_hand = i          # 왼손 위치
        elif i in [3, 6, 9]:    # 3, 6, 9는 오른손
            answer += "R"
            r_hand = i          # 오른손 위치
        else:
            if i==0: i=11       # 0은 11로 간주
            l_abs = abs(i-l_hand)   # 누를 숫자-왼손 숫자의 절대값
            r_abs = abs(i-r_hand)   # 누를 숫자-오른손 숫자의 절대값
            if sum(divmod(l_abs, 3)) < sum(divmod(r_abs, 3)):   # 차이값을 3으로 나누었을 때 몫과 나머지의 합이 낮은 쪽이 가까운 곳
                answer += 'L'
                l_hand = i
            elif sum(divmod(l_abs, 3)) > sum(divmod(r_abs, 3)):
                answer += 'R'
                r_hand = i
            else:                   # 왼손, 오른손 거리가 동일 할 경우
                if hand=='left':    # 왼손 잡이는 왼손
                    answer += 'L'
                    l_hand = i
                else:
                    answer += 'R'   # 오른손 잡이는 오른손
                    r_hand = i
    return answer
```


```python
solution([1, 3, 4, 5, 8, 2, 1, 4, 5, 9, 5], "right")
```




    'LRLLLRLLRRL'




```python
solution([7, 0, 8, 2, 8, 3, 1, 5, 7, 6, 2], "left")
```




    'LRLLRRLLLRR'




```python
solution([1, 2, 3, 4, 5, 6, 7, 8, 9, 0], "right")
```




    'LLRLLRLLRL'