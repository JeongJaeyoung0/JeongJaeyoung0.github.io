---
layout: post
title: "[Coding test] Programmers_level 2_스킬트리"
subtitle: "ProgrammersLevel-2-25"
categories: python
tags: codingtest
comments: true
---

* 문제 요약 : 선행 스킬 순서 skill과 유저들이 만든 스킬트리1를 담은 배열 skill_trees가 매개변수로 주어질 때, 가능한 스킬트리 개수를 반환

```python
def solution(skill, skill_trees):
    # 가능한 개수
    answer = 0
    # 스킬 트리 반복문
    for trees in skill_trees:
        # 스킬트리 문자 하나씩 반복하여 스킬에 존재할 경우 리스트로 담은 후 join
        tree = ''.join([t for t in trees if t in skill])
        # 스킬중 트리의 길이만큼의 값과 트리가 같을 경우
        if skill[0:len(tree)] == tree:
            # +1
            answer += 1 
    return answer
```

```python
>>> solution("CBD", ["BACDE", "CBADF", "AECB", "BDA"])
2
>>> solution("CBD", ["CAD"])
0
```