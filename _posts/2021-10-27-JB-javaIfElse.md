---
layout: post
title: "[기초] 자바 조건문"
subtitle: "javaIfElse"
categories: java
tags: basicsJava
comments: true
---

# 조건문 

* if 문
    ``` java
    if(조건식) {
        수행문;
    }
    ```

* if-else 문
    ``` java
    if(조건식) {
        수행문1;
    } else {
        수행문2;
    }
    ```

* if-else if-else 문
    ``` java
    if(조건1) {
        수행1;
    } else if(조건2) {
        수행2;
    } else if(조건3) {
        수행3;
    } else {
        수행4;
    }
    ```

* 조건 연산자
    ``` java
    max = (a > b) ? a : b;
    ```

* switch-case 문
    ``` java
    if(rank == 1) {
        medalColor = 'G';
    } else if(rank == 2) {
        medalColor = 'S';
    } else if(rank == 3) {
        medalColor = 'B';
    } else {
        medalColor = 'A';
    }
    ```

    ``` java
    switch(rank) {
        case 1 : medalColor = 'G';
            break;
        case 2 : medalColor = 'S';
            break;
        case 3 : medalColor = 'B';
            break;
        default : medalColor = 'A';
    }
    ```