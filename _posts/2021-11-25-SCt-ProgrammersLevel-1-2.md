---
layout: post
title: "[Coding test] Programmers_level 1_없는 숫자 더하기"
subtitle: "ProgrammersLevel-1-2"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 0부터 9까지의 숫자 중 일부가 들어있는 numbers 배열에서 찾을 수 없는 수를 더하여 반환 

```swift
func solution(_ numbers:[Int]) -> Int {
    // 반환할 sum 변수 생성
    var sum: Int = 0
    // 1부터 9까지 for문
    for x in 0...9{
        // x값이 numbers 배열에 없을 경우
        if !(numbers.contains(x)) {
            // sum에 추가
            sum = sum + x
        }
    }
    return sum
}
```

```swift
func solution(_ numbers: [Int]) -> Int {
    // 0부터 9까지 숫자를 filter로 numbers 배열에 없는 경우를 배열로 만들고, 그 배열의 합을 반환
    return (0...9).filter { !numbers.contains($0) }.reduce(0, +)
}
```