---
layout: post
title: "[Coding test] Programmers_level 1_자연수 뒤집어 배열로 만들기"
subtitle: "ProgrammersLevel-1-15"
categories: swift
tags: codingTestSwift
comments: true
---

* 문제 요약 : 자연수 n을 뒤집어 배열 형태로 반환

```swift
func solution(_ n:Int64) -> [Int] {
    return String(n).map {Int(String($0))!}.reversed()
}
```