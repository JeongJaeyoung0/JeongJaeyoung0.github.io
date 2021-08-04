---
layout: post
title: "[Crawling] AirKorea"
subtitle: "Airkorea"
categories: python
tags: crawling
comments: true
---

* 수집: 미세먼지 측정정보
* 코딩: [github](https://github.com/JeongJaeyoung0/crawling/blob/a485bfbb92341f81981ce183e163908e5df67387/crawling_airkorea.ipynb "github")

<br>

# ● code

***

# crawling_airkorea
step 1. 에어코리아 > 일평균, 년, 월, 대전 선택 > 검색 > 엑셀
### step 0. 준비


```python
import sys   # 시스템
import os    # 시스템

import pandas as pd   # 판다스 : 데이터분석 라이브러리
import numpy as np    # 넘파이 : 숫자, 행렬 데이터 라이브러리

from bs4 import BeautifulSoup   # html 데이터를 전처리
from selenium import webdriver   # 웹 브라우저 자동화
import time                      # 서버와 통신할 때 중간중간 시간 지연
import datetime                  # 날짜 계산
from tqdm import tqdm_notebook   # for문 돌릴 때 진행상황을 %게이지로 알려줌
```

### step 1. 크롤링


```python
driver = webdriver.Chrome(r"./chromedriver/chromedriver.exe")

# 사이트 주소
driver.get("https://www.airkorea.or.kr/web/pmRelay?itemCode=11008&pMENU_NO=109")
time.sleep(2)
```


```python
# 일평균 클릭
driver.find_element_by_css_selector("#strDateDiv2").click()
```


```python
# 년도 선택
#for i1 in range(1, len(yyyy)+1):
# 20번 이상 검색하면 에러 발생, 그래서 1년단위로 함
for i1 in [6]:   # 1=2021, 2=2020, 3=2019...
    element1 = "/html/body/div[4]/div[2]/div[2]/form/div/span[2]/select[1]/option[{}]".format(i1)
    driver.find_element_by_xpath(element1).click()
    time.sleep(0.2)
    
    # 월 계산
    mm = driver.find_element_by_css_selector("#searchDate_mm").text.split()
    mm = mm[1:13]
    mm

    # 월 선택
    for i2 in range(2, len(mm)+2):
        element2 = "/html/body/div[4]/div[2]/div[2]/form/div/span[2]/select[2]/option[{}]".format(i2)
        driver.find_element_by_xpath(element2).click()
        time.sleep(0.2)
        
        # 지역 선택
        element3 = "/html/body/div[4]/div[2]/div[2]/form/div/select"
        driver.find_element_by_xpath(element3).click()
        
        # 검색 클릭
        driver.find_element_by_css_selector(".search").click()
        time.sleep(12)
        
        # 엑셀 클릭
        driver.find_element_by_css_selector(".xls").click()
        time.sleep(3)
```


```python

```
