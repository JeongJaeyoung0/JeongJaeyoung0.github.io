---
layout: post
title: "[Coding test] Programmers_level 1_직사각형 별찍기"
subtitle: "ProgrammersLevel-1-6"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : *을 가로 길이가 n, 세로 길이가 m인 직사각형 형태로 출력

```swift
import Foundation

let n = readLine()!.components(separatedBy: [" "]).map { Int($0)! }
let (a, b) = (n[0], n[1])

for _ in 1...b {
    // *을 a개수만큼 줄바꾸지 않고 출력
    for _ in 1...a { print("*", terminator: "") }
    // b만큼 줄 바꿈
    print("")
}
```

```swift
import Foundation

let n = readLine()!.components(separatedBy: [" "]).map { Int($0)! }
let (a, b) = (n[0], n[1])

// b만큼 반복
for _ in 1...b {
    // *을 a개수 만큼 배열을 만들고 join하여 출력
    print(Array(repeating: "*", count: a).joined())
}
```