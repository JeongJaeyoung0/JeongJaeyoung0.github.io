---
layout: post
title: "[Coding test] Programmers_level 1_크레인 인형뽑기 게임"
subtitle: "ProgrammersLevel-1-2"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/0ded0da5f23d3928144e7123a2974c713a245323/210616_Programmers_level%201_%ED%81%AC%EB%A0%88%EC%9D%B8%20%EC%9D%B8%ED%98%95%EB%BD%91%EA%B8%B0%20%EA%B2%8C%EC%9E%84.ipynb)

***

# Programmers_level 1_크레인 인형뽑기 게임
### n번째, n-1번째 뽑은 인형이 같으면 터지며, 터진 인형 수 출력


```python
def solution(board, moves):
    basket=[0]      # 인형을 담을 basket list
    answer=0        # 터진 인형 수
    for i in moves: # 뽑을 인형 리스트 for문
        for j in range(len(board)):     # 뽑을 인형 상위에서 아래로 for문
            move = board[j][i-1]        # board의 j행, i열
            if move!=0:                 # 인형이 존재하는 행 확인
                if basket[-1]==move:    # 지금 뽑은 인형이 직전에 뽑은 인형이랑 같은지 비교
                    del basket[-1]      # 같을 경우 직전에 뽑은 인형 터트리고
                    answer+=2           # 터진 인형은 +2개
                else:
                    basket+=[move]      # 직전에 뽑은 인형과 같지 않을경우
                board[j][i-1]=0         # 뽑은 인형 자리를 0으로 대체
                break                   # if문 빠져나가기
    return answer                       # 정답 return
```


```python
solution([[0,0,0,0,0],[0,0,1,0,3],[0,2,5,0,1],[4,2,4,4,2],[3,5,1,3,1]], [1,5,3,5,1,2,1,4])
```




    4