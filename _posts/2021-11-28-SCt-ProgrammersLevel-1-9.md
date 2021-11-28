---
layout: post
title: "[Coding test] Programmers_level 1_행렬의 덧셈"
subtitle: "ProgrammersLevel-1-9"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : arr1, arr2의 행렬의 덧셈을 반환

```swift
func solution(_ arr1:[[Int]], _ arr2:[[Int]]) -> [[Int]] {
    // 결과 행렬 초기화
    var result: [[Int]] = []
    // arr1, arr2 행렬 for문
    for (ar1, ar2) in zip(arr1, arr2) {
        // 덧셈을 저장할 행렬 초기화
        var sumArr: [Int] = []
        // arr1, arr2안의 배열을 for문
        for (a1, a2) in zip(ar1, ar2) {
            // 각 덧셈을 추가
            sumArr.append(a1 + a2)
        }
        // 한 행씩 결과를 추가
        result.append(sumArr)
    }
    return result
}
```

```swift
func solution(_ arr1:[[Int]], _ arr2:[[Int]]) -> [[Int]] {
    return zip(arr1, arr2).map{zip($0,$1).map{$0+$1}}
}
```