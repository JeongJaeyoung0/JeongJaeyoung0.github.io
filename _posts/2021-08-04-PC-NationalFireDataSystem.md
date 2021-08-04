---
layout: post
title: "[Crawling] 소방청 국가화재정보센터"
subtitle: "NationalFireDataSystem"
categories: python
tags: crawling
comments: true
---

* 수집: 화재 현황
* 코딩: [github](https://github.com/JeongJaeyoung0/crawling/blob/d9b6d9ff1a723260bba709534ba0c655dcf708ce/crawling_%EC%86%8C%EB%B0%A9%EC%B2%AD_%EA%B5%AD%EA%B0%80%ED%99%94%EC%9E%AC%EC%A0%95%EB%B3%B4%EC%84%BC%ED%84%B0.ipynb "github")

<br>

# ● code

***

# crawling_소방청 국가화재정보센터
step 1. 소방청 > 시작 날짜 입력, 끝 날짜 입력, 지역 선택, 검색 클릭 > 크롤링 > 엑셀 저장
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
driver.get("http://nfds.go.kr/dashboard/status.do")
time.sleep(2)
```


```python
day = []
fire = []
die = []
injury = []
property_damage = []
```


```python
# 검색 시작 날짜
keyword = datetime.datetime(2021,1,1)
```


```python
# 크롤링
while keyword < datetime.datetime(2021,1,11):   # 검색 끝 날짜+1
    
    keyword1 = keyword.strftime('%Y%m%d')
    day.append(keyword1)

    # 날짜 입력 1
    element1 = driver.find_element_by_css_selector("#search-startDate > input")
    element1.clear()
    element1.send_keys(keyword.strftime("%y %m %d"))

    # 날짜 입력 2
    element2 = driver.find_element_by_css_selector("#search-endDate > input")
    element2.clear()
    element2.send_keys(keyword.strftime("%y %m %d"))

    # 대전 지역 선택
    element3 = driver.find_element_by_xpath("/html/body/div/div[3]/div/div/div[3]/div[2]/select/option[7]").click()

    # 검색 클릭
    search_button = driver.find_element_by_css_selector(".glyphicon.glyphicon-search").click()
    time.sleep(2)

    # 화재발생건수 크롤링
    fire_day = driver.find_element_by_css_selector("#crnt_tc")
    fire.append(fire_day.text)
    fire

    # 인명피해사망 크롤링
    die_day = driver.find_element_by_css_selector("#crnt_dc")
    die.append(die_day.text)
    die

    # 인명피해부상 크롤링
    injury_day = driver.find_element_by_css_selector("#crnt_lc")
    injury.append(injury_day.text)
    injury

    # 재산피해 크롤링
    property_damage_day = driver.find_element_by_css_selector("#crnt_fd")
    property_damage.append(property_damage_day.text)
    property_damage
    
    print(keyword.strftime("%y %m %d"), fire_day.text, die_day.text, injury_day.text, property_damage_day.text)
    
    keyword = keyword + datetime.timedelta(days=1) # 다음 날
```

    21 01 01 5 0 0 1,208,632
    21 01 02 2 0 0 1,441
    21 01 03 2 0 0 3,917
    21 01 04 3 0 0 14,800
    21 01 05 3 0 0 10,500
    21 01 06 2 0 0 977
    21 01 07 3 0 0 1,477
    21 01 08 5 0 3 4,076
    21 01 09 7 0 0 9,775
    21 01 10 3 0 0 17,409
    


```python
# 판다스화
df = pd.DataFrame({'날짜':day, '화재발생건수':fire, '인명피해사망':die, '인명피해부상':injury, '재산피해(천원)':property_damage})
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>날짜</th>
      <th>화재발생건수</th>
      <th>인명피해사망</th>
      <th>인명피해부상</th>
      <th>재산피해(천원)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20210101</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>1,208,632</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20210102</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>1,441</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20210103</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>3,917</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20210104</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>14,800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>20210105</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>10,500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>20210106</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>977</td>
    </tr>
    <tr>
      <th>6</th>
      <td>20210107</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>1,477</td>
    </tr>
    <tr>
      <th>7</th>
      <td>20210108</td>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>4,076</td>
    </tr>
    <tr>
      <th>8</th>
      <td>20210109</td>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>9,775</td>
    </tr>
    <tr>
      <th>9</th>
      <td>20210110</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>17,409</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 엑셀 저장
df.to_excel('소방청_화재현황_20160101-20201231.xlsx')
```


```python

```
