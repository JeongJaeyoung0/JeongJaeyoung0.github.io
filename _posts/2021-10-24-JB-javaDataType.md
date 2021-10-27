---
layout: post
title: "[기초] 자바 자료형 (변수, 상수, 형변환)"
subtitle: "javaDataType"
categories: java
tags: basicsJava
comments: true
---

# 변수
* 변수 : 변하는 값

    * 자료형

    ||정수형|문자형|실수형|논리형|
    |:---:|:---:|:---:|:---:|:---:|
    |1바이트 (-2^7 ~ 2^7-1)|byte|-|-|**boolean**|
    |2바이트 (-2^15 ~ 2^15-1)|short|**char**|-|-|
    |4바이트 (-2^31 ~ 2^31-1)|**int**|-|float|-|
    |8바이트 (-2^63 ~ 2^63-1)|long|-|**double**|-|
    
    * 32 비트를 초과하는 숫자는 long 형으로 처리해야 함
        ```java
        long num = 12345678900L;
        ```

    * 실수는 기본적으로 double로 처리 함
        ```java
        float fnum = 3.14F;
        ```

    * 자료형 없이 변수 사용 (자바 10부터, 지역변수에서만 사용 가능)
        ```java
        var num = 10;
        var dNum = 10.0;
        var str = "hello";
        ```

* * *
<br>
# 상수
* 상수 : 변하지 않는 값
    ```java
    final double PI = 3.141592;
    ```

* * *
<br>
# 형 변환
* 서로 다른 자료형의 값이 대입되는 경우 형 변환이 일어 남

    * 묵시적 형 변환 : 작은 수 에서 큰 수로 대입되는 경우
        ```java
        long lNum = 10;
        float fNum = lNum;
        ```

    * 명시적 형 변환 : 큰 수에서 작은 수로 대입되는 경우
        ```java
        double dNum = 3.141592;
        int iNum = (int)dNum;
        ```