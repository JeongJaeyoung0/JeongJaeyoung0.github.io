---
layout: post
title: "[Coding test] Programmers_level 1_하샤드 수"
subtitle: "ProgrammersLevel-1-11"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : x의 자리수 합으로 x가 나누어 지는지 반환

```swift
func solution(_ x:Int) -> Bool {
    // 숫자 각 자리별로 배열로 변환
    let arr = String(x).compactMap{ $0.wholeNumberValue }
    // 배열의 합이 x로 나누어 몫이 0인지 판별
    return x % arr.reduce (0, +) == 0
}
```

```swift
func solution(_ x:Int) -> Bool {
    return x % String(x).reduce(0, {$0+Int(String($1))!}) == 0
}
```