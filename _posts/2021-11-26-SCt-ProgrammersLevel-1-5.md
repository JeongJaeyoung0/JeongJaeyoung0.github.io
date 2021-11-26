---
layout: post
title: "[Coding test] Programmers_level 1_신규 아이디 추천"
subtitle: "ProgrammersLevel-1-5"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 신규 유저가 규칙에 맞지 않는 아이디를 입력할 경우 유사하면서 규칙에 맞는 추천 아이디를 반환
* 규칙 : 아이디 길이: 3~15 / 알파벳 소문자, 숫자, 빼기, 밑줄, 마침표만 사용 가능 / 단 마침표는 처음과 끝에 사용할 수 없으며 또한 연속 사용 불가

```swift
func solution(_ new_id:String) -> String {
    // 1단계. 소문자로 치환
    var newId1: String = new_id.lowercased()
    // 2단계. 소문자, 숫자, "-", "_", "."을 제외한 문자 제거
    newId1 = String(newId1.filter { "abcdefghijklmnopqrstuvwxyz0123456789-_.".contains($0) })
    // 문자열을 각각 배열로
    var newId2 = newId1.unicodeScalars.map(String.init)
    // 3단계. "."가 2개 이상 연속되면 1개로 치환
    var i = 1
    if newId2.count>1 {
        while i < newId2.count-1{
            if newId2[i-1] == "." && newId2[i] == "." {
                newId2.remove(at: i-1)
                i -= 1
            }
            i += 1
        }
        // 4단계. "."가 처음에 있으면 제거
        if newId2[0] == "." {
            newId2.remove(at: 0)
        }
    }
    // 4단계. "."가 끝에 있으면 제거
    if newId2[newId2.count-1] == "." {
        newId2.remove(at: newId2.count-1)
    }
    // 5단계. 빈 문자열이면 "a"를 대입
    if newId2.count == 0 {
        newId2.append("a")
    }
    // 6단계. 길이가 16이상 일 경우 16 이상 문자 제거
    if newId2.count > 15 {
        newId2 = [String](newId2[0...14])
    }
    // 제거한 후 마지막 자리가 "."일 경우 제거
    if newId2[newId2.count-1] == "." {
        newId2.remove(at: newId2.count-1)
    }
    // 7단계. 길이가 2개 이하일 경우 마지막 자리를 길이가 3이 될 때 까지 반복
    while newId2.count < 3  {
        newId2.append(newId2[newId2.count-1])
    }
    // join하여 반환
    return newId2.joined()
}
```