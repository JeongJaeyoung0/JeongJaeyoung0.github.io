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
    // 최소값 구하기
    let minNum = arr.min()!
    // 배열중 최소값과 일치 하지 않는것만 filter하여 result에 저장
    var result = arr.filter { $0 != minNum }
    // 배열이 비어있다면 [-1]을 반환하고, 아니면 배열을 반환
    return result.isEmpty ? [-1] : result
}
```