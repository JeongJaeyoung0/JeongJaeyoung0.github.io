---
layout: post
title: "[Crawling] Google Image"
subtitle: "GoogleImage"
categories: python
tags: crawling
comments: true
---

* 수집: 이미지
* 코딩: [github](https://github.com/JeongJaeyoung0/crawling/blob/48afc2413bb957c0e8d51bb5e9cfe4c8617d8d96/crawling_google_image.ipynb "github")

<br>

# ● code

***

# crawling_google image
Step 1. 구글 검색 > 이미지 > 이미지 저장
### step 0. 준비


```python
import pandas as pd
import numpy as np
import os
import urllib.request

from selenium import webdriver
from tqdm import tqdm
import time
from time import sleep
```

### step 1. 이미지 크롤링


```python
# 크롤링 할 검색어, 이미지 개수
keyword = input("크롤링할 검색어 입력: ")
image_num = int(input("크롤링할 이미지 개수: "))
```


```python
%%time
# 폴더 생성
if not os.path.exists("image_google_"+keyword):
    os.makedirs("image_google_"+keyword)
# 크롬창 띄우기
driver = webdriver.Chrome(r"./chromedriver/chromedriver.exe")
driver.get("https://www.google.com/search?q=%s"%keyword)
time.sleep(1)
# 이미지 클릭
driver.find_element_by_css_selector("#hdtb-msb > div:nth-child(1) > div > div:nth-child(3) > a").click()
# 첫 번째 사진 클릭
driver.find_element_by_xpath("/html/body/div[2]/c-wiz/div[3]/div[1]/div/div/div/div[1]/div[1]/span/div[1]/div[1]/div[1]/a[1]/div[1]/img").click()

count = 0
for i in range(image_num):
    # 이미지 URL get
    imgURL = driver.find_element_by_xpath("/html/body/div[2]/c-wiz/div[3]/div[2]/div[3]/div/div/div[3]/div[2]/c-wiz/div/div[1]/div[1]/div[2]/div[1]/a/img").get_attribute("src")
    # 이미지 저장 (파일명 중복 확인 중복이면 count 1씩 증가)
    swich = 'on'
    while swich == 'on':
        if not os.path.exists("image_google_{0}/image_google_{0}_{1} ({2}).jpg".format(keyword, count, i)):
            urllib.request.urlretrieve(imgURL, "image_google_{0}/image_google_{0}_{1} ({2}).jpg".format(keyword, count, i))
            swich = 'off'
        else: count += 1
    # 다음 이미지
    driver.find_element_by_xpath("/html/body/div[2]/c-wiz/div[3]/div[2]/div[3]/div/div/div[3]/div[2]/c-wiz/div/div[1]/div[1]/div[1]/div/div[3]/a[2]/svg").click()
    time.sleep(0.5)

driver.close()
```
