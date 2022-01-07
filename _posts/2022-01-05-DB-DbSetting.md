---
layout: post
title: "[DB] DB 설정 방법"
subtitle: "DbSetting"
categories: webapp
tags: db
comments: true
---

# DB 설계 방법
  - Tool: MySQL Workbench(6.x ver), HeidiSQL, MariaDB
  - 방법: MySQL로 설계 후 HeidiSQL로 사용(Diagram으로 보기 위함)

## DB 설계 순서
1. MySQL에서 테이블 설계  
    - Datatype 설명
        - VARCHAR: text길이 지정한 만큼 입력(지정 길이보다 짧게 입력하면 그 길이만큼만 저장)
        - CHAR: text길이 지정한 만큼 입력(지정 길이보다 짧아도 공백을 채워서 저장)
        - TEXT: text길이 지정하지 않음 (2Gb? 입력 가능)
        - DATE: 년원일
        - TIME: 시분초
        - DATATIME: 년월일시분초
        - TIMESATMP: 1970/01/01 기준으로 흐른 시간(단위: 초)

    - Datatype 예시
        - 제목: VARCHAR(255)
        - 내용: TEXT
        - 날짜: DATATIME
        - 기타: VARCHAR(45)
        - FilePata: VARCHAR(255)
        - Email: VARCHAR(320)
        - YN: VARCHAR(1) #Bool, Int 보다 VARCHAR(1)로 "Y", "N"으로 구분하는 것이 좋음 (언어에 따라 True, T, Yes 등 다르기 때문)

2. 설계 후 Forward
 - Database > Forward Engineer > SSL > Use SSL: No

3. HeidiSQL로 열기
 - New (포트 번호 등 입력)