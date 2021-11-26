---
layout: post
title: "[Coding test] Programmers_level 1_나머지가 1이 되는 수 찾기"
subtitle: "ProgrammersLevel-1-7"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 자연수 n을 x로 나눈 나머지가 1이 되는 수 중 가장 작은 자연수 x를 반환

```swift
import Foundation

func solution(_ n:Int) -> Int {
    // 1부터 n중 나머지가 0이되는 필터를 거친 배열 중 첫번째를 반환
    return (1...n).filter { n % $0 == 1 }[0]
}
```

```swift
import Foundation

func solution(_ n:Int) -> Int {
    // 1부터 n미만 까지 for문
    for i in 1..<n {
        // 나머저ㅣ가 1이 되면 i를 반환
        if n % i == 1 { return i }
    }
    // 그렇지 않으면 n-1을 반환
    return n - 1
}
```