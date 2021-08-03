---
layout: post
title: "[Setting] KoNLPy 설치 방법 (자연어처리, NLP)"
subtitle: "konlpyinstall"
categories: python
tags: setting
comments: true
---

# KoNLPy 설치 방법
### 한글 자연어 처리하기 위한 프로그램

* * *

1. cmd
2. pip 업그레이드
```python
pip install -upgrade pip
```
3. [오라클 JDK 다운로드](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html, "오라클 JDK 다운로드") (운영 체재, 시스템 정류에 맞게)
4. 설치
5. window키 > 시스템 환경 변수 편집 > 환경 변수 > 시스템 변수 > 새로만들기
    * 변수 이름: `JAVA_HOME`
    * 변수 값(jvm.dll이 있는 폴더): `C:\Program Files\Java\jdk1.8.0_291\jre\bin\server`
6. cmd
7. konlpy 인스톨
```python
pip install konlpy
```
8. 파이썬에서 비트, 버전 확인
```python
import platform
print(platform.architecture())
!python --version
```
9. [jpype1 다운로드](https://www.lfd.uci.edu/~gohlke/pythonlibs/, "jpype1 다운로드")
    * ex) Python 3.8.5 / 64bit의 경우 JPype1-1.2.0-cp38-cp38-win32.whl
10. 파이썬 실행되는 경로에 파일 이동
11. 파이썬에서 아래 명령어 실행
```python
pip install JPype1-1.1.2-cp38-cp38-win_amd64.whl --user
```
12. 정상 설치 확인 방법
```python
import konlpy
print(konlpy.__version__)
```