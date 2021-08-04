---
layout: post
title: "[Crawling] Instagram"
subtitle: "Instagram"
categories: python
tags: crawling
comments: true
---

* 수집: 이미지
* 코딩: [github](https://github.com/JeongJaeyoung0/crawling/blob/0a387ec96fc62d2cf7f861832124d7035e4b9699/crawling_instagram.ipynb "github")

<br>

# ● code

***

# crawling_instagram
Step 1. 인스타 > 검색어 입력 > 첫번째 검색어 선택 > 사진 클릭 > 데이터 수집
Step 2. 이미지 저장할 폴더 생성 > 이미지 저장
### step 0. 준비


```python
import pandas as pd
import numpy as np

from selenium import webdriver
from selenium.webdriver import ActionChains as AC
from tqdm import tqdm
from tqdm import tqdm_notebook
import re
from time import sleep
import time
```

### step 1. 크롤링


```python
# 검색어
keyword = input("크롤링할 키워드를 입력하세요: ")
len_insta = int(input("크롤링할 글 수를 입력하세요: "))
```

    크롤링할 키워드를 입력하세요: 테슬라
    크롤링할 글 수를 입력하세요: 10
    


```python
# 크롬창 띄우기
driver = webdriver.Chrome(r"./chromedriver/chromedriver.exe")
driver.get("https://www.instagram.com/")
time.sleep(2)
```
수동 로그인

```python
dict = {}   # 전체 데이터를 담을 딕셔너리 생성

# 검색창에 커서 클릭
element = driver.find_element_by_css_selector(".pbgfb.Di7vw")
element.click()
time.sleep(1)

# 검색 창에 검색어 입력
element = driver.find_element_by_css_selector(".XTCLo.x3qfX")
element.send_keys(keyword)
time.sleep(3)

# 검색어 리스트 중 첫번째 검색어 클릭
query_list = driver.find_elements_by_css_selector(".-qQT3")
query_list[0].click()
time.sleep(7)

# 사진 클릭
CSS_tran="div.Nnq7C.weEfm"                                      # 사진 버튼 정의 
tran_button = driver.find_element_by_css_selector(CSS_tran)     # 사진 버튼 찾기
AC(driver).move_to_element(tran_button).click().perform()       # 사진 버튼 클릭
time.sleep(1)

# 크롤링 시작
for i in tqdm_notebook(range(0, len_insta)):

    target_info = {}                                            # 사진별 데이터를 담을 딕셔너리 생성

    try:
        # 사진(pic) 크롤링 시작
        overlays1 = "div._2dDPU.CkGkG .FFVAD"                   # 사진창 속 사진   
        img = driver.find_element_by_css_selector(overlays1)    # 사진 선택
        pic = img.get_attribute('src')                          # 사진 url 크롤링 완료
        target_info['picture'] = pic
        # print(target_info)

        # 날짜(date) 크롤링 시작
        overlays2 = "div._2dDPU.CkGkG .c-Yi7 > time"                # 날짜 지정
        datum2 = driver.find_element_by_css_selector(overlays2)     # 날짜 선택
        date = datum2.get_attribute('title')
        # get_attribute('title')                                    # 날짜 크롤링 완료
        target_info['date'] = date
        # print(target_info)
        # print(datalist)

        # 좋아요(like) 크롤링 시작
        overlays3 = ".Nm9Fw"                                        # 리뷰창 속 날짜
        datum3 = driver.find_element_by_css_selector(overlays3)     # 리뷰 선택
        like = datum3.text                                          # 좋아요 크롤링 완료
        target_info['like'] = like
        # print(target_info)

        # 해시태그(tag) 크롤링 시작
        overlays4 = ".C7I1f.X7jCj"                                  # 태그 지정
        datum3 = driver.find_element_by_css_selector(overlays4)     # 태그 선택
        tag_raw = datum3.text
        tags = re.findall('#[A-Za-z0-9가-힣]+', tag_raw)            # ""#OOO"만 뽑아오기(OOO: 한글,숫자,영어,_)
        tag = ''.join(tags).replace("#"," ")                        # "#" 제거
        target_info['tag'] = tag
        # print(target_info)

        dict[i] = target_info            # 토탈 딕셔너리로 만들기

        print("{0}".format(i), tag)

        # 다음장 클릭
        CSS_tran2="a._65Bje.coreSpriteRightPaginationArrow"             # 다음 버튼 정의
        tran_button2 = driver.find_element_by_css_selector(CSS_tran2)  # 다음 버튼 find
        AC(driver).move_to_element(tran_button2).click().perform()     # 다음 버튼 클릭
        time.sleep(2)

    except:  # 에러가 나면
        # 다음장 클릭
        CSS_tran2="a._65Bje.coreSpriteRightPaginationArrow"             # 다음 버튼 정의
        tran_button2 = driver.find_element_by_css_selector(CSS_tran2)  # 다음 버튼 find
        AC(driver).move_to_element(tran_button2).click().perform()     # 다음 버튼 클릭
        time.sleep(2)

driver.close()

print(dict)

# 판다스화
import pandas as pd
result_df = pd.DataFrame.from_dict(dict, 'index')

n = result_df['picture'].count()

# 엑셀 저장
result_df.to_excel("insta_({}).xlsx".format(keyword), encoding='euc-kr')
```

    <ipython-input-6-321d5a58edbb>:25: TqdmDeprecationWarning: This function will be removed in tqdm==5.0.0
    Please use `tqdm.notebook.tqdm` instead of `tqdm.tqdm_notebook`
      for i in tqdm_notebook(range(0, len_insta)):
    


    HBox(children=(HTML(value=''), FloatProgress(value=0.0, max=10.0), HTML(value='')))


    1  테슬라모델3퍼포먼스 풀옵 슈퍼카
    2  테슬라 모델3 승차감
    3 
    4  테슬라 테슬라x
    5  테슬라 엠프 미러볼 라운딩 아일랜드cc 씨드느와골프웨어 씨드느와크루 씨드느와
    6  테슬라 테슬라주식 미국주식 미국주식멘탈이전부다 주식스타그램 주식공부 투자 투자자
    7  테슬라 테슬라주식 미국주식 미국주식멘탈이전부다 주식스타그램 주식고수 주식공부 주식투자 주식초보
    8  instaseoul teslamodel3 igerskorea tesla model3 teslife autopilot autosteer fsd follow francais 캠린이 노을 노을맛집
    9  냉동실이름모를생선을구워 슬기로운음주생활 하이트진로 테라 참이슬 대구경북주부서포터즈 진로이즈백 필라이트 테진아 테슬라 hjdk 청정맥주 리얼탄산100 국산맥주 1위맥주 1초26병판매 집콕맥주 혼맥 홈맥 여행맥주 진로 소통 좋아요 팔로우늘리기 좋아요반사 좋반 좋아요늘리기 일상 좋아요꾹 먹스타그램
    
    {1: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/207813720_345853870378094_998024562957257922_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=102&_nc_ohc=DeSQK5toPwEAX_Tfh8U&edm=AP_V10EBAAAA&ccb=7-4&oh=b0bc4cad5b42267d7bfc7ffb8925b482&oe=61109481&_nc_sid=4f375e', 'date': '2021년 6월 26일', 'like': '좋아요 121개', 'tag': ' 테슬라모델3퍼포먼스 풀옵 슈퍼카'}, 2: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/s1080x1080/226192442_548491083017145_5771935671359482490_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=109&_nc_ohc=QPxA7MU0zWwAX9jWB93&tn=NEgSdiv0AOcwBior&edm=AP_V10EBAAAA&ccb=7-4&oh=4884e686ac85fcb390da44360cb27853&oe=61107E53&_nc_sid=4f375e', 'date': '2021년 7월 27일', 'like': '좋아요 1,291개', 'tag': ' 테슬라 모델3 승차감'}, 3: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/s1080x1080/218329494_519478395929559_7373639783916036746_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=103&_nc_ohc=JCcnSeDMo00AX8h5LyA&edm=AP_V10EBAAAA&ccb=7-4&oh=facbc6357c7a1ad5952620ee499ab3a9&oe=61110CC2&_nc_sid=4f375e', 'date': '2021년 7월 15일', 'like': '좋아요 378개', 'tag': ''}, 4: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/p1080x1080/208977555_117880710541167_6013402833390566943_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=103&_nc_ohc=09q17qrVQj0AX-P_ETT&tn=NEgSdiv0AOcwBior&edm=AP_V10EBAAAA&ccb=7-4&oh=d424d1979cb16f744b643ed91cb2f217&oe=6111D51F&_nc_sid=4f375e', 'date': '2021년 7월 3일', 'like': '좋아요 8,722개', 'tag': ' 테슬라 테슬라x'}, 5: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/p1080x1080/211307441_5798648360206995_4159368297176218424_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=103&_nc_ohc=cwtoBDEuS2MAX-ZCx4f&edm=AP_V10EBAAAA&ccb=7-4&oh=075df5e1192a2f5bf6430ce19b9013da&oe=6110A3FB&_nc_sid=4f375e', 'date': '2021년 7월 7일', 'like': '좋아요 430개', 'tag': ' 테슬라 엠프 미러볼 라운딩 아일랜드cc 씨드느와골프웨어 씨드느와크루 씨드느와'}, 6: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/s1080x1080/231644605_1254479781648134_2275939647611951165_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=102&_nc_ohc=okOl5n3yUW4AX-_paJa&edm=AP_V10EBAAAA&ccb=7-4&oh=b9c869600be8e322db77787ad56ca669&oe=6111E074&_nc_sid=4f375e', 'date': '2021년 8월 3일', 'like': '좋아요 506개', 'tag': ' 테슬라 테슬라주식 미국주식 미국주식멘탈이전부다 주식스타그램 주식공부 투자 투자자'}, 7: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/s1080x1080/232310749_183576700499070_1849644019163834273_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=106&_nc_ohc=KwPO8P5XTCQAX94Nm--&edm=AP_V10EBAAAA&ccb=7-4&oh=5d57ad0a8e0fcc35d4456f30e4c37420&oe=61126C51&_nc_sid=4f375e', 'date': '2021년 8월 4일', 'like': '좋아요 361개', 'tag': ' 테슬라 테슬라주식 미국주식 미국주식멘탈이전부다 주식스타그램 주식고수 주식공부 주식투자 주식초보'}, 8: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/p1080x1080/231348913_1014597756024114_2513007949117605440_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=106&_nc_ohc=-He8y_-VKfwAX-UAkfe&edm=AP_V10EBAAAA&ccb=7-4&oh=e91694bd2eac3dae632989cef13e0d89&oe=611258E2&_nc_sid=4f375e', 'date': '2021년 8월 4일', 'like': '좋아요 14개', 'tag': ' instaseoul teslamodel3 igerskorea tesla model3 teslife autopilot autosteer fsd follow francais 캠린이 노을 노을맛집'}, 9: {'picture': 'https://scontent-ssn1-1.cdninstagram.com/v/t51.2885-15/e35/s1080x1080/231067798_800119240651220_4910897878813882239_n.jpg?_nc_ht=scontent-ssn1-1.cdninstagram.com&_nc_cat=108&_nc_ohc=8fCiyV_qq0AAX_e5tUQ&edm=AP_V10EBAAAA&ccb=7-4&oh=5acc7abb66e6a18e771387e58bfaeb44&oe=61107581&_nc_sid=4f375e', 'date': '2021년 8월 4일', 'like': '좋아요 13개', 'tag': ' 냉동실이름모를생선을구워 슬기로운음주생활 하이트진로 테라 참이슬 대구경북주부서포터즈 진로이즈백 필라이트 테진아 테슬라 hjdk 청정맥주 리얼탄산100 국산맥주 1위맥주 1초26병판매 집콕맥주 혼맥 홈맥 여행맥주 진로 소통 좋아요 팔로우늘리기 좋아요반사 좋반 좋아요늘리기 일상 좋아요꾹 먹스타그램'}}
    


```python
result_df
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
      <th>picture</th>
      <th>date</th>
      <th>like</th>
      <th>tag</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 6월 26일</td>
      <td>좋아요 121개</td>
      <td>테슬라모델3퍼포먼스 풀옵 슈퍼카</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 7월 27일</td>
      <td>좋아요 1,291개</td>
      <td>테슬라 모델3 승차감</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 7월 15일</td>
      <td>좋아요 378개</td>
      <td></td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 7월 3일</td>
      <td>좋아요 8,722개</td>
      <td>테슬라 테슬라x</td>
    </tr>
    <tr>
      <th>5</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 7월 7일</td>
      <td>좋아요 430개</td>
      <td>테슬라 엠프 미러볼 라운딩 아일랜드cc 씨드느와골프웨어 씨드느와크루 씨드느와</td>
    </tr>
    <tr>
      <th>6</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 8월 3일</td>
      <td>좋아요 506개</td>
      <td>테슬라 테슬라주식 미국주식 미국주식멘탈이전부다 주식스타그램 주식공부 투자 투자자</td>
    </tr>
    <tr>
      <th>7</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 8월 4일</td>
      <td>좋아요 361개</td>
      <td>테슬라 테슬라주식 미국주식 미국주식멘탈이전부다 주식스타그램 주식고수 주식공부 주식...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 8월 4일</td>
      <td>좋아요 14개</td>
      <td>instaseoul teslamodel3 igerskorea tesla model...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>https://scontent-ssn1-1.cdninstagram.com/v/t51...</td>
      <td>2021년 8월 4일</td>
      <td>좋아요 13개</td>
      <td>냉동실이름모를생선을구워 슬기로운음주생활 하이트진로 테라 참이슬 대구경북주부서포터즈...</td>
    </tr>
  </tbody>
</table>
</div>




```python
num_pic = len(result_df['picture'])
num_pic
```




    9



### step 2. 이미지 저장


```python
# 이미지들 image_insta 폴더에 다운받기
import os
import urllib.request

# 만약 폴더가 없으면 생성
if not os.path.exists("image_insta_"+keyword):  #if not () 없으면
    os.makedirs("image_insta_"+keyword)         # 생성

# 이미지 저장
for i in range(0, 50):
    try:
        index = result_df['picture'][i]
        date = result_df['date'][i]
        urllib.request.urlretrieve(index, "image_insta_{0}/{1}_{2}.jpg".format(keyword, i, date))        
    except:
        pass
```


```python

```
