---
layout: post
title: "[기초] 자바 자료형"
subtitle: "javaDataType"
categories: java
tags: basicsJava
comments: true
---

## 자료형

||정수형|문자형|실수형|논리형|
|---|---|---|---|---|
|1바이트|byte|-|-|**boolean**|
|2바이트|short|**char**|-|-|
|4바이트|**int**|-|float|-|
|8바이트|long|-|**double**|-|

* 32 비트를 초과하는 숫자는 long 형으로 처리해야 함
    ```java
    long num = 12345678900**L**;
    ```

* 실수는 기본적으로 double로 처리 함
    ```java
    float fnum = 3.14**F**
    ```

* 자료형 없이 변수 사용 (자바 10부터)
    * 지역변수에서만 사용 가능
    ```java
    var num = 10;
    var dNum = 10.0;
    var str = 'hello';
    ```