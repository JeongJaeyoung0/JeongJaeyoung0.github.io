---
layout: post
title: "[Coding test] Programmers_level 2_괄호 회전하기"
subtitle: "ProgrammersLevel-2-27"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 문자열 s가 주어질 때, 첫번째 문자를 문자열 마지막으로 반복 이동하였을 때 올바른 괄호 문자열이 되는 경우의 수를 반환

```python
def solution(s):
    # 반환값 초기화
    answer = 0
    # 첫번째 문자를 마지막으로 이동할 경우의 수 만큼 for문
    for _ in range(len(s) - 1):
        # 문자열 담을 리스트 초기화
        l = []
        # s의 문자 하나씩 for문
        for i, a in enumerate(s):
            # (, {, [ 일 경우 리스트에 추가
            if a == "(" or a == "{" or a == "[":
                l.append(a)
            # ), }, ] 일 경우
            else:
                try:
                    # ) 일 경우
                    if a == ")":
                        # 이전이 ( 일 경우
                        if l[-1] == "(":
                            # ( 를 리스트에서 삭제
                            l.pop()
                        else:
                            # 그렇지 않을 경우 종료
                            break
                    # } 일 경우 동일
                    elif a == "}":
                        if l[-1] == "{":
                            l.pop()
                        else:
                            break
                    # ] 일 경우 동일
                    else:
                        if l[-1] == "[":
                            l.pop()
                        else:
                            break
                # 처음부터 닫는 괄호일 경우
                except:
                    break
        # 마지막 문자까지 돌았고, 리스트에 아무것도 남아있지 않을 경우 True로 +1
        answer += (i == len(s) - 1 and len(l) == 0)
        
        s = s[1:] + s[0]
    return answer
```

```python
>>> solution("[](){}")
3

>>> solution("}]()[{")
2

>>> solution"[)(]")
0

>>> solution("}}}")
0
```