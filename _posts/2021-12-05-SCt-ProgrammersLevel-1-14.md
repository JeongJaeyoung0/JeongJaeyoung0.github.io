---
layout: post
title: "[Coding test] Programmers_level 1_정수 제곱근 판별"
subtitle: "ProgrammersLevel-1-14"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : n이 x의 제곱이라면 x+1의 제곱을 반환, 아니라면 -1을 반환

```swift
import Foundation

func solution(_ n:Int64) -> Int64 {
    // 루트n
    var root  = sqrt(Double(n))
    // root를 하나씩 배열화
    var str = String(root).map { $0 }
    // 배열의 마지막이 "0"일 경우
    if str.last == "0" {
        // root + 1의 제곱을 반환
        return Int64(pow(Double(root + 1), 2.0))
    }
    else {
        return -1
    }
}
```

```swift
import Foundation

func solution(_ n:Int64) -> Int64 {
    let t = Int64(sqrt(Double(n)))
    return t * t == n ? (t+1)*(t+1) : -1
}
```