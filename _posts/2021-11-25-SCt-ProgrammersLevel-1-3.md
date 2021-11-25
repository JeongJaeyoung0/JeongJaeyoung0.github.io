---
layout: post
title: "[Coding test] Programmers_level 1_두 개 뽑아서 더하기"
subtitle: "ProgrammersLevel-1-3"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 정수 배열 numbers에서 서로 다른 인덱스의 두 수를 뽑아 더하여 만들 수 있는 모든 수를 오름차순 배열로 반환

```swift
func solution(_ numbers:[Int]) -> [Int] {
    // 빈 Set 생성
    var result = Set<Int>()
    // 첫 번째 수 인덱스 for문
    for i in 0...(numbers.count - 2) {
        // 두 번째 수 인덱스 for문
        for j in (i + 1)...(numbers.count - 1) {
            // 두 수를 더하여 set에 insert
            result.insert(numbers[i] + numbers[j])
        }
    }
    // 오름차순 정렬하여 반환
    return result.sorted()
}
```