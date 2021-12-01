---
layout: post
title: "[Coding test] Programmers_level 1_콜라츠 추측"
subtitle: "ProgrammersLevel-1-12"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 조건에 만족하는 반복 횟수를 반환. 단, 500번을 반복해도 성립되지 않으면 -1을 반환.
* 조건
    * 1-1. 입력된 수가 짝수라면 2로 나눈다.
    * 1-2. 입력된 수가 홀수라면 3을 곱하고 1을 더한다.
    * 2. 결과로 나온 수에 같은 작업을 1이 될 떄까지 반복한다.

```swift
func solution(_ num:Int) -> Int {
    var result: Int = num
    var cnt: Int = 0
    
    while result != 1 {
        if result % 2 == 0 {
            result /= 2
        }
        else {
            result = result * 3 + 1
        }
        cnt += 1
        if cnt == 501 {
            return -1
        }
    }
    return cnt
}
```

```swift
func solution(_ x:Int) -> Bool {
    return x % String(x).reduce(0, {$0+Int(String($1))!}) == 0
}
```