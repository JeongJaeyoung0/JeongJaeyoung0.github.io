---
layout: post
title: "[Coding test] Programmers_level 2_주식가격"
subtitle: "ProgrammersLevel-2-25"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 초 단위로 기록된 주식가격이 담긴 배열 prices가 매개변수로 주어질 때, 가격이 떨어지지 않은 기간은 몇 초인지를 반환

```python
def solution(prices):
    # 반환할 리스트
    answer = []
    # 0 ~ 길이만큼 반복문
    for i in range(len(prices)):
        # 초 카운트
        cnt = 0
        # 현재+1 ~ 길이만큼 반복문
        for j in range(i+1, len(prices)):
            # 다음값이 크거나 같을 경우
            if prices[i] <= prices[j]:
                # 카운트 +1
                cnt += 1
            # 다음값이 작을 경우
            else:
                # 카운트 +1
                cnt += 1
                # 반복문 종료
                break
        # 카운트 값 리스트에 추가
        answer.append(cnt)
    # 반환
    return answer
```

```python
>>> solution([1, 2, 3, 2, 3])
[4, 3, 1, 1, 0]
``` 