---
layout: post
title: "[Crawling] Youtube"
subtitle: "youtube(selenium)"
categories: python
tags: crawling
comments: true
---

* 수집: 제목, 조회수, 날짜, 좋아요, 싫어요, 댓글
* 코딩: [github](https://github.com/JeongJaeyoung0/crawling/blob/a458bd86ebf3e05e9f9735669faa79f5aa0c5f80/crawling_youtube(selenium).ipynb "github")

<br>

# ● code

***

# crawling_youtube
step 1. url 수집: 검색어 입력, 크롤링 글 개수 입력
step 2. 크롤링: 제목, 조회수, 날짜, 좋아요, 싫어요, 댓글
### step 0. 준비


```python
import sys    # 시스템
import os     # 시스템

import pandas as pd    # 판다스 : 데이터분석 라이브러리
import numpy as np     # 넘파이 : 숫자, 행렬 데이터 라이브러리

from selenium import webdriver    # 웹 브라우저 자동화
import time                       # 시간 지연
import math                       # 올림, 내림
from selenium.webdriver.common.keys import Keys
from tqdm import tqdm   # 진행상황 표시
```

### step 1. url 수집


```python
keyword = input('검색어 입력: ')
articles_number = int(input('크롤링 글 개수: '))
```

    검색어 입력: 일기예보
    크롤링 글 개수: 5
    


```python
# 크롬 웹브라우저 실행
driver = webdriver.Chrome(r"./chromedriver/chromedriver.exe")

# 키워드로 접속
driver.get("https://www.youtube.com/results?search_query={}".format(keyword))
time.sleep(2)
```


```python
# 스크롤 다운 함수
def scroll_down(driver):
    driver.execute_script("window.scrollTo(0, 99999)")
    time.sleep(2)
```


```python
# 영상 목록 스크롤 다운 실행
for i in range(math.ceil((articles_number-26)/20)):
    scroll_down(driver)
```


```python
crawling_list = []
url_list = []

# url 수집
crawling_list = driver.find_elements_by_tag_name('h3 > a')

for crawling in crawling_list:
    url = crawling.get_attribute('href')   
    url_list.append(url)
driver.close()
url_list = url_list[:articles_number]
print('크롤링할 글 수: ', len(url_list))
url_list[0]
```

    크롤링할 글 수:  5
    




    'https://www.youtube.com/watch?v=V2XYfgef1kU'



### step 2. 크롤링


```python
%%time
dict = {}
count = 0

for url in tqdm(url_list):
    # url 열기
    driver = webdriver.Chrome(r"./chromedriver/chromedriver.exe")
    driver.get(url)
    time.sleep(2)

    driver.execute_script("window.scrollTo(0, 400)")
    time.sleep(1)
    
    info = driver.find_element_by_css_selector('.style-scope ytd-video-primary-info-renderer').text.split('조회수')

    # 제목
    title = info[0].split('\n')[-2]
    
    # 조회수, 날짜 위치 추출
    for i in info[1].split('\n'):
        if '회' in i:
            view_date = i

    # 조회수
    #view = int(view_date[0].split('•')[0].replace('회', '').replace(',',''))
    view = int(view_date.split('•')[0].replace('회', '').replace(',',''))
    # 날짜
    #date = view_date[0].split('•')[1]
    date = view_date.split('•')[1]
    # 좋아요
    like = info[1].split('\n')[1]
    # 싫어요
    dont_like = info[1].split('\n')[2]

    try:
        # 댓글 수
        review_cnt = driver.find_element_by_xpath('/html/body/ytd-app/div/ytd-page-manager/ytd-watch-flexy/div[5]/div[1]/div/ytd-comments/ytd-item-section-renderer/div[1]/ytd-comments-header-renderer/div[1]/h2/yt-formatted-string/span[2]').text.replace(',', '')
        print('<',count,'>', title, '( 댓글 수:', review_cnt,')')
        
        # 댓글 스크롤 다운
        for i in range(math.ceil((int(review_cnt)-20)/20)):
            scroll_down(driver)
        print('1. 스크롤 다운 완료')
        
        # 광고 끄기
        time.sleep(10)
        try:
            driver.find_element_by_css_selector("#main > div > ytd-button-renderer").click()
            print('2. 광고 창 제거함')
        except:
            print('2. 광고 창 안뜸')
        
        try:
            # 답글 n개 보기 클릭
            buttons = driver.find_elements_by_css_selector("#more-replies > a")
            for button in buttons:
                button.send_keys(Keys.ENTER)
                time.sleep(1)
                button.click()
            time.sleep(1)
            print('3. 답글 보기 클릭 완료')
        except:
            print('3. 답글 보기 없음')
        
        try:
            # 답글 더보기 클릭
            buttons_more = driver.find_elements_by_css_selector('#continuation > yt-next-continuation > tp-yt-paper-button')
            for button in buttons_more:
                button.send_keys(Keys.ENTER)
                time.sleep(1)
            print('4. 답글 더보기 클릭 완료')
        except:
            print('4. 답글 더보기 없음')
        
        # 댓글 수집
        review_list = []
        reviews = driver.find_elements_by_css_selector('#content-text')
        for review in reviews:
            review = review.text
            review_list.append(review)
        print('5. 댓글 수집 :', len(review_list))
            
    except:
        review_cnt = ''
        review_list = ''
        print('댓글 차단')
            
    target_info = {}
    target_info['제목'] = title
    target_info['조회수'] = view
    target_info['날짜'] = date
    target_info['좋아요'] = like
    target_info['싫어요'] = dont_like
    target_info['댓글 수'] = review_cnt
    target_info['댓글'] = review_list

    dict[count] = target_info

    driver.close()
    count += 1
    time.sleep(1)
```

      0%|                                                                                            | 0/5 [00:00<?, ?it/s]

    < 0 > [내일날씨] 내일과 모레 전국 많은 비, 천둥·번개 유의, 5월 14일 17시 기준 ( 댓글 수: 4 )
    1. 스크롤 다운 완료
    2. 광고 창 안뜸
    3. 답글 보기 클릭 완료
    4. 답글 더보기 클릭 완료
    5. 댓글 수집 : 4
    

     20%|████████████████▊                                                                   | 1/5 [00:18<01:14, 18.67s/it]

    < 1 > [내일날씨] 내일 새벽~오전 중부지방 강하고 많은 비, 5월 15일 17시 기준 ( 댓글 수: 9 )
    1. 스크롤 다운 완료
    2. 광고 창 안뜸
    3. 답글 보기 클릭 완료
    4. 답글 더보기 클릭 완료
    5. 댓글 수집 : 9
    

     40%|█████████████████████████████████▌                                                  | 2/5 [00:42<01:00, 20.21s/it]

    < 2 > [MV] 일기예보(日氣豫報 /Weather Forecast) - 인형의 꿈 ( 댓글 수: 80 )
    1. 스크롤 다운 완료
    2. 광고 창 제거함
    3. 답글 보기 클릭 완료
    4. 답글 더보기 클릭 완료
    5. 댓글 수집 : 80
    

     60%|██████████████████████████████████████████████████▍                                 | 3/5 [01:21<00:51, 25.75s/it]

    < 3 > [날씨] 내일 고온 절정…주말 장마전선 반짝 북상? (2021.05.13/뉴스데스크/MBC) ( 댓글 수: 27 )
    1. 스크롤 다운 완료
    2. 광고 창 제거함
    3. 답글 보기 클릭 완료
    4. 답글 더보기 클릭 완료
    5. 댓글 수집 : 26
    

     80%|███████████████████████████████████████████████████████████████████▏                | 4/5 [01:51<00:27, 27.06s/it]

    < 4 > [날씨박사] 봄철 또 다른 불청객 '꽃가루'…예보부터 대처까지 / JTBC 뉴스룸 ( 댓글 수: 2 )
    1. 스크롤 다운 완료
    2. 광고 창 제거함
    3. 답글 보기 클릭 완료
    4. 답글 더보기 클릭 완료
    5. 댓글 수집 : 2
    

    100%|████████████████████████████████████████████████████████████████████████████████████| 5/5 [02:10<00:00, 26.04s/it]

    Wall time: 2min 10s
    

    
    


```python
# 판다스화
df = pd.DataFrame.from_dict(dict, 'index')
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
      <th>제목</th>
      <th>조회수</th>
      <th>날짜</th>
      <th>좋아요</th>
      <th>싫어요</th>
      <th>댓글 수</th>
      <th>댓글</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>[내일날씨] 내일과 모레 전국 많은 비, 천둥·번개 유의, 5월 14일 17시 기준</td>
      <td>2607</td>
      <td>2021. 5. 14.</td>
      <td>83</td>
      <td>6</td>
      <td>4</td>
      <td>[자세한 일기 예보 감사 합니다, 아휴, 자세한 일기 예보 감사합니다., 아주 브리...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>[내일날씨] 내일 새벽~오전 중부지방 강하고 많은 비, 5월 15일 17시 기준</td>
      <td>2791</td>
      <td>2021. 5. 15.</td>
      <td>99</td>
      <td>1</td>
      <td>9</td>
      <td>[전남은 비가 많이 안 올까요...?, 제주도 애월은 비도안오더라 ㅅㅂ, 오늘은 대...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>[MV] 일기예보(日氣豫報 /Weather Forecast) - 인형의 꿈</td>
      <td>233389</td>
      <td>2015. 8. 17.</td>
      <td>1천</td>
      <td>49</td>
      <td>80</td>
      <td>[Known this song for  several years but it's m...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>[날씨] 내일 고온 절정…주말 장마전선 반짝 북상? (2021.05.13/뉴스데스크...</td>
      <td>24902</td>
      <td>2021. 5. 13.</td>
      <td>319</td>
      <td>6</td>
      <td>27</td>
      <td>[5/14일 장마전선 북상 베트남이야?\n🇰🇷인되.., 지구 온난화로 인해서 날씨가...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>[날씨박사] 봄철 또 다른 불청객 '꽃가루'…예보부터 대처까지 / JTBC 뉴스룸</td>
      <td>1804</td>
      <td>2021. 5. 13.</td>
      <td>21</td>
      <td>0</td>
      <td>2</td>
      <td>[경북쪽은   끝난지가 언젠데\n이제방송하는걸보니\n우리나라가  넓은가보네, 「나쁜...</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 엑셀 저장
df.to_excel('crawler_youtube_review_{}.xlsx'.format(keyword))
```


```python

```
