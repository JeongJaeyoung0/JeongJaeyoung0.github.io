---
layout: post
title: "[Coding test] Programmers_level 1_제일 작은 수 제거하기"
subtitle: "ProgrammersLevel-1-4"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 정수 배열 중 가장 작은 수를 제거한 배열을 반환

```swift
func solution(_ arr:[Int]) -> [Int] {
    var result = arr.filter { $0 != arr.min()! }
    return result.isEmpty ? [-1] : result
}
```