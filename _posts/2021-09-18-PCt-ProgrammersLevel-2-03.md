---
layout: post
title: "[Coding test] Programmers_level 2_오픈채팅방"
subtitle: "ProgrammersLevel-2-03"
categories: python
tags: codingTestPython
comments: true
---

* 문제 요약 : 채팅방에 들어오고 나가거나, 닉네임을 변경한 기록이 담긴 문자열 배열 record가 매개변수로 주어질 때, 모든 기록이 처리된 후, 최종적으로 방을 개설한 사람이 보게 되는 메시지를 문자열 배열 형태로 반환

```python
def solution(record):
    result_id = [] # id로 결과 저장할 리스트
    result_nick = [] # 최종 결과 반환할 리스트
    id = {} # id, nickname 담을 딕셔너리
    for r in record:
        r = r.split() # 문장을 분할
        if r[0] == 'Enter': # 분할된 문장의 첫 단어가 'Enter'일 경우
            id[r[1]] = r[2] # 딕셔너리 key는 문장의 1번째 단어(id), value는 2번째 단어(nickname)
            result_id.append('%s님이 들어왔습니다.' % r[1]) # 'id님이 들어왔습니다.' 추가
        elif r[0] == 'Leave': # 분할된 문장의 첫 번째 단어가 'Leave'일 경우
            result_id.append('%s님이 나갔습니다.' % r[1]) # 'id님이 나갔습니다.' 추가
        else: # 분할된 문장의 첫 번째 단어가 'Change'일 경우
            id[r[1]] = r[2] # 딕셔너리 key 값을 교체
    for i in result_id: # id로 저장된 리스트를 nickname으로 교체 작업
        user_id = i.split('님')[0] # '님'을 기준으로 분할하고 0 번째(id)를
        result_nick.append(i.replace(str(user_id),id[user_id])) # 문자열 변환(id > nickname) 하여 리스트에 추가
    return result_nick
```

```python
>>> solution(["Enter uid1234 Muzi", "Enter uid4567 Prodo","Leave uid1234","Enter uid1234 Prodo","Change uid4567 Ryan"])
["Prodo님이 들어왔습니다.", "Ryan님이 들어왔습니다.", "Prodo님이 나갔습니다.", "Prodo님이 들어왔습니다."]
``` 