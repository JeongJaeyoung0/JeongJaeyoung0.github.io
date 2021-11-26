---
layout: post
title: "[Coding test] Programmers_level 1_x만큼 간격이 있는 n개의 숫자"
subtitle: "ProgrammersLevel-1-8"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 정수 x와 자연수 n을 x부터 시작해 x씩 증가하는 숫자를 n개 지니는 배열을 반환

```swift
func solution(_ x:Int, _ n:Int) -> [Int64] {
    // x씩 증가하는 결과를 담을 변수
    var x1: Int64 = Int64(x)
    // 반환할 배열
    var result: [Int64] = []
    // 1부터 n까지 for문
    for _ in 1...n {
        // x1을 배열에 추가
        result.append(x1)
        // x만큼씩 증가
        x1 += Int64(x)
    }
    return result
}
```

```swift
func solution(_ x:Int, _ n:Int) -> [Int64] {
    // 1부터 n까지 map으로 반복 > $0 * x를 Int64로 형변환 > 배열로 반환
    return Array(1...n).map { Int64($0 * x) }
}
```