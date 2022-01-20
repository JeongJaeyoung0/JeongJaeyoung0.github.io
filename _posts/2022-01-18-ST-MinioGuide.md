---
layout: post
title: "[Storage] miniO 가이드"
subtitle: "MinioGuide"
categories: other
tags: minio
comments: true
---
# miniO guide

## miniO 설치 및 설정
1. minio server 폴더 생성
  ```
  mkdir D:/minio
  cd D:/minio
  ```

2. miniO 다운로드
  - https://min.io/download#/windows
  - D:\minio 에 다운로드

3. miniO 설정
  ```
  D:\minio\minio.exe server D:\minio --console-address ":9001"
  ```

4. API 주소에 들어가서 로그인
  - API: {http://192...}
  - RootUser: minioadmin
  - RootPass: minioadmin

5. Create Bucket

6. Create User
  - 권한 부여(Policy)

* * *

## 데이터 송수신 방법
1. S3 Browser 설치

2. Account 추가
  - Accounts > Add new accounts
    - Display name: {name 입력}
    - Account type: S3 Compatible Storage
    - REST Endpoint: {minio 4번의 API 주소 입력}
    - Access Key ID: {User ID}
    - Secret Access Key: {Use Key}
    - Use secure transfer (SSL/TLS): 체크 여부 확인 {test용 pc는 해제해도 됨}

3. Account > Display name 클릭 