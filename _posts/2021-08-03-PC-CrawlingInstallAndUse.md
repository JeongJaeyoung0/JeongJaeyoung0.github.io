---
layout: post
title: "[Crawling] Crawling install 및 사용법"
subtitle: "CrawlingInstallAndUse"
categories: python
tags: crawling
comments: true
---

* Selenium 설치 (cmd)

```python
pip install selenium
pip install regex               # 제거
pip install times
pip install tqdm
```
<br>

* Library import

```python
import sys						# 시스템
import os						# 시스템

from selenium import webdriver	# 웹 브라우저 자동화
from bs4 import BeautifulSoup	# html 데이터를 전처리

from selenium.webdriver import ActionChains as AC	# 웹 브라우저 동작
from tqdm import tqdm
from tqdm import tqdm_notebook	# for문 돌릴 때 진행상황을 %게이지로 알려줌
from tqdm.notebook import tqdm
from time import sleep
import time						# 서버와 통신할 때 중간중간 시간 지연
import re						# 해시태그(#) 제거
```
<br>

* Chrome driver 경로 지정 경로 (r"경로")

```python
driver = webdriver.Chrome(r"G:\내 드라이브\exe\chromedriver.exe")
```
<br>

* Elements 입력 방법

```python
element = driver.find_element_by_css_selector("#id")
element = driver.find_element_by_css_selector(".class")
element = driver.find_element_by_xpath("우클릭 > Copy > Copy full Xpath")
element = driver.find_element_by_link_text(text)
element = driver.find_element_by_name(name)
element = driver.find_element_by_id(id)
```
<br>

* 함수

```python
# 검색 클릭
A.submit()

# 버튼 클릭
.click()

# text 확인
.text

# 속성값 확인
.get_attribute


# 하위 탭
# ▼ <A>
#   ▼ <B>
#     <c de>
('.A .B > c.de')
```