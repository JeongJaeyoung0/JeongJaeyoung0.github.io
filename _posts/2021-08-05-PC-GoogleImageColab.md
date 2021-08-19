---
layout: post
title: "[Crawling] Google image(colab)"
subtitle: "GoogleImageColab"
categories: python
tags: crawling
comments: true
--- 

* 수집: 이미지
* 코딩: [github](https://github.com/JeongJaeyoung0/crawling/blob/b4922bb10ff6f696413e300895f83a50524001bb/crawling_google_image(colab).ipynb "github")

<br>

<table align="left">
  <td>
        <a target="_blank" href="https://colab.research.google.com/github/JeongJaeyoung0/crawler/blob/main/210708_crawler_google_image(colab).ipynb"><img src="https://www.tensorflow.org/images/colab_logo_32px.png"/>구글 코랩에서 실행하기</a>
  </td>
</table>

<br>
<br>
<br>
<br>

# ● code

***

```python
from google.colab import drive
drive.mount('/content/drive')
```

    Drive already mounted at /content/drive; to attempt to forcibly remount, call drive.mount("/content/drive", force_remount=True).
    

# crawling_google image(colab)

### step 0. 준비


```python
!pip install selenium
!apt-get update
!apt install chromium-chromedriver
```


```python
from selenium import webdriver
import os
from tqdm import tqdm
import time
```

### step 1. 이미지 크롤링


```python
# 크롤링 할 검색어, 이미지 개수
keyword = input("크롤링할 검색어 입력: ")
image_num = int(input("크롤링할 이미지 개수: "))
```

    크롤링할 검색어 입력: 우주 성운
    크롤링할 이미지 개수: 500
    


```python
# 크롬창 띄우기
chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless')
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')
driver = webdriver.Chrome('chromedriver', chrome_options=chrome_options)
driver.get("https://www.google.com/search?q=%s&source=lnms&tbm=isch&sa=X&ved=2ahUKEwj_weCY6M7xAhUHhZQKHRgRDy0Q_AUoAXoECAEQAw&biw=1920&bih=937"%keyword)
time.sleep(1)

# 첫 번째 사진 클릭
driver.find_element_by_css_selector(".rg_i.Q4LuWd").click()
time.sleep(1)

# url 수집
img_url = []
for i in tqdm(range(image_num)):
    # 이미지 url get
    time.sleep(1)
    url = driver.find_element_by_css_selector(".n3VNCb").get_attribute("src")
    if i != 0 and url == img_url[-1]:
        print('\n더이상 수집할 데이터가 없음')
        break
    img_url.append(url)

    # 다음 이미지
    if i == 0:
        element = driver.find_element_by_css_selector(".gvi3cf")
        driver.execute_script("arguments[0].click();", element)
    time.sleep(1)
    element = driver.find_element_by_css_selector(".gvi3cf")
    driver.execute_script("arguments[0].click();", element)

# 크롬창 종료
driver.close()

print('수집된 url 개수 :', len(img_url))
```

    /usr/local/lib/python3.7/dist-packages/ipykernel_launcher.py:6: DeprecationWarning: use options instead of chrome_options
      
    100%|██████████| 500/500 [02:25<00:00,  3.43it/s]

    수집된 url 개수 : 500
    

    
    


```python
# 저장된 이미지 제거
#!rm -rf "/content/images" #다운로드 받은 이미지 폴더(base_dir의 주소) 전체 제거
#!rm -rf "/content/images/폴더명" #다운로드 받은 이미지 폴더에서 "폴더명"에 해당하는 폴더 전체 제거
```


```python
# HTTP Error 403 해결
import random
import urllib.request

opener=urllib.request.build_opener()
opener.addheaders=[('User-Agent','Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/36.0.1941.0 Safari/537.36')]
urllib.request.install_opener(opener)

# 폴더 생성
if not os.path.exists("images"):
    os.makedirs("images")

if not os.path.exists("./images/"+keyword):
    os.makedirs("./images/"+keyword)

# 이미지 저장
count = 0
err_img_url = []
for n, i in enumerate(img_url):
    try:
        urllib.request.urlretrieve(i, "./images/{0}/{0}_{1}.jpg".format(keyword, count))
        count += 1
        if n!=0 and n%50==0:
            print(n, "/", len(img_url), "개 완료")
    except:
        err_img_url.append(i)
        print("error 발생으로 수집안됨 (번호: %d)" % n)   # 주로 503 error, error 발생시 수동으로 이미지 저장 (  img_url[error No.]  )
print('\n저장된 이미지 개수 :', count, '\n')
print('에러 이미지 URL:')
for i in err_img_url:
    print(i)
```

    50 / 500 개 완료
    100 / 500 개 완료
    150 / 500 개 완료
    200 / 500 개 완료
    250 / 500 개 완료
    300 / 500 개 완료
    350 / 500 개 완료
    400 / 500 개 완료
    450 / 500 개 완료
    
    저장된 이미지 개수 : 500 
    
    에러 이미지 URL:
    

### step 2. 저장


```python
# 크롤링한 이미지 폴더 압축
import zipfile
 
fantasy_zip = zipfile.ZipFile('/content/crawler_google_image.zip', 'w') # 압축 후 저장 위치
for folder, subfolders, files in os.walk('/content/images'): # 압축 할 폴더
    for file in files:
        if file.endswith('.jpg'): # 압축할 파일 확장자
            fantasy_zip.write(os.path.join(folder, file), os.path.relpath(os.path.join(folder,file), '/content/images/'), compress_type = zipfile.ZIP_DEFLATED)
fantasy_zip.close()
```


```python
# 압축 파일 구글 드라이브에 복사
!cp '/content/crawler_google_image.zip' '/content/drive/MyDrive/Colab Notebooks/crawler_google_image.zip'
```
