---
layout: post
title: "[Coding test] Programmers_level 1_짝수와 홀수"
subtitle: "ProgrammersLevel-1-13"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 정수 num가 짝수일 경우 "Even", 홀수인 경우 "Odd"를 반환.

```swift
func solution(_ num:Int) -> String {
    return num % 2 == 0 ? "Even" : "Odd"
}
```