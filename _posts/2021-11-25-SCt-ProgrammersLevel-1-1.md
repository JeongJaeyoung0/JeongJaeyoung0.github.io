---
layout: post
title: "[Coding test] Programmers_level 1_평균 구하기"
subtitle: "ProgrammersLevel-1-1"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : arr 배열의 평균값을 반환

```swift
func solution(_ arr:[Int]) -> Double {
    // 배열의 합을 Double로 변환하고, 배열의 크기를 Double로 변환하여 나누어 반환
    return Double(arr.reduce(0, +)) / Double(arr.count)
}
```