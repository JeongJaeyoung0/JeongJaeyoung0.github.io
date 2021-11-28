---
layout: post
title: "[Coding test] Programmers_level 1_핸드폰 번호 가리기"
subtitle: "ProgrammersLevel-1-10"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 전화번호의 뒷 4자리를 제외한 나머지 숫자를 "*"로 가린 문자열을 반환

```swift
func solution(_ phone_number:String) -> String {
    // 결과 담을 변수 초기화
    var result: String = ""
    // 번호 for문
    for (i, s) in phone_number.enumerated() {
        // 번호 길이보다 -4 미만인 경우 "*" 추가
        if i < phone_number.count - 4 { result.append("*") }
        // 이상인 경우 문자열 그대로 추가
        else {result.append(s)}
    }    
    return result
}
```

```swift
func solution(_ phone_number:String) -> String {
    // count 만큼 repeating 반복 + 뒷 4자리 추가하여 반환
    return String(repeating:"*", count:phone_number.count-4)+phone_number.suffix(4)
}
```