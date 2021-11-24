---
layout: post
title: "[Coding test] Programmers_level 1_K번째"
subtitle: "ProgrammersLevel-1-8"
categories: python
tags: codingTestPython
comments: true
---

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/dbed44a5fabca51d00cc410c84d02473e6f64384/210622_Programmers_level%201_K%EB%B2%88%EC%A7%B8%EC%88%98.ipynb)

***

# Programmers_level 1_K번째수
### i번째부터, j번째까지의 수를 정렬하고 k번째 수를 출력


```python
def solution(array, commands):
    return [sorted(array[i-1:j])[k-1] for i, j, k in commands]
```


```python
solution([1, 5, 2, 6, 3, 7, 4], [[2, 5, 3], [4, 4, 1], [1, 7, 3]])
```




    [5, 6, 3]