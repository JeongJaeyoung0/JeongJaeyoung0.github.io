---
layout: post
title: "[Coding test] Baekjoon_level 11_브루트 포스-2"
subtitle: "BaekjoonLevel11-2"
categories: python
tags: codingtest
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/5d94525dbea18f2e564e82ffead3e4fa5562960e/210610_Baekjoon_coding%20test_level%2011_%EB%B8%8C%EB%A3%A8%ED%8A%B8%20%ED%8F%AC%EC%8A%A4-2.ipynb)

***

2021.06.10
# coding test_Baekjoon_level 11_브루트 포스-2


```python
# 1018 (체스판 다시 칠하기)-1
def c_color(pan) :
    cnt = 0
    cc = pan[0][0]
    for i in range(len(pan)) :
        for j in range(0, len(pan[i]), 2) :
            if pan[i][j] != cc : cnt += 1
            if pan[i][j+1] == cc : cnt += 1
        if cc == 'B' : cc = 'W'
        else : cc = 'B'   
    return cnt

row, col = map(int, input().split())
csp = [input().strip() for _ in range(row)]
ans = []
for i in range(len(csp)-7) :
    for j in range(len(csp[i])-7) :
        bod = [r[j:j+8] for r in csp[i:i+8]]
        ans.append(c_color(bod))
print(min(min(ans), 64-max(ans)))
```

    8 8
    WBWBWBWB
    BWBWBWBW
    WBWBWBWB
    BWBBBWBW
    WBWBWBWB
    BWBWBWBW
    WBWBWBWB
    BWBWBWBW
    1
    


```python
# 1018 (체스판 다시 칠하기)-2
N,M=map(int,input().split())
r=range
L=[[ord(c)+i+j&1for j,c in enumerate(input())]for i in r(N)]
print(min(32-abs(sum(4-sum(l[j:j+8])for l in L[i:i+8]))for i in r(N-7)for j in r(M-7)))
```

    8 8
    WBWBWBWB
    BWBWBWBW
    WBWBWBWB
    BWBBBWBW
    BWBWBWBW
    WBWBWBWB
    WBWBWBWB
    WBWBWBWB
    25
    


```python
# 1436 (영화감독 숌)
print([i for i in range(2666800) if '666' in str(i)][int(input())-1])
```

    10000
    2666799