---
layout: post
title: "[Wordcloud] Kakao talk"
subtitle: "KakaoTalk"
categories: python
tags: textanalysis
comments: true
---

* 코딩: [github](https://github.com/JeongJaeyoung0/text_analysis/blob/97d1418978beea10307fb4121e9448c163ea544b/wordcloud_kakao_talk.ipynb "github")

<br>

# ● code

***

# wordcloud_kakao_talk

### step 0. 준비


```python
import scipy as sp
import pandas as pd
import numpy as np
import re
import collections

# konlpy 한글 텍스트 분석 패키지
from konlpy.tag import Kkma       ; kkma = Kkma()
from konlpy.tag import Hannanum   ; hannanum = Hannanum()
from konlpy.tag import Okt        ; t = Okt()
from konlpy.tag import *
import pickle # 모델 파일 저장

from sklearn.feature_extraction.text import CountVectorizer
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression
from sklearn.pipeline import Pipeline
from sklearn.metrics import accuracy_score
from sklearn.model_selection import train_test_split

# 그래프
%matplotlib inline
import os
import matplotlib.pyplot as plt
import seaborn as sns
import graphviz
from sklearn.tree import export_graphviz

# 그래프 문자 깨지는 것 대처
import matplotlib
from matplotlib import font_manager, rc
import platform
if platform.system() == 'Windows':
# 윈도우인 경우
    font_name = font_manager.FontProperties(fname="c:/Windows/Fonts/malgun.ttf").get_name()
    rc('font', family=font_name)
else:
# Mac 인 경우
    rc('font', family='AppleGothic')

# 워닝 없애주는 것
import warnings  
warnings.filterwarnings('ignore')
```

### step 1. 전처리


```python
file = open("kakao_talk.txt", "r+", encoding='UTF8')
```


```python
# 줄 수
strings = file.readlines()
del strings[0:7]
print(len(strings))
#strings
```


```python
name_list = []
text_list = []
```


```python
# 전처리
for i in range(0, len(strings)):
    # 시간 삭제
    num_del = re.sub(r'\d','',strings[i]).replace('.','').replace('\n','')
    num_del = num_del.split(':')
    
    # 시작 글이 날짜가 아닌 데이터들 처리
    if strings[i][0:2] == '20':
        if ':' in strings[i]:
            name_list.append(num_del[1].replace(',','').replace(' ',''))
            text_list.append(num_del[2])
    else:
        name_list.append('')
        text_list.append(num_del[0])
```


```python
# 길이가 다르면 문제 있음
print(len(name_list))
print(len(text_list))
```


```python
# 판다스화
df = pd.DataFrame({'name': name_list, 'text': text_list})
df
```


```python
# 이름 빈칸을 윗칸의 이름으로 채우기
for i in range(0, len(df)):
    if df.name[i] == '':
        df.name[i] = df.name[i-1]
df
```


```python
# 이름별 채팅 수 카운트
df.name.value_counts()
```

### step 2. matplot


```python
# column 그래프 그리기(필수)
plt.figure(figsize=(8, 6))                 # 그래프 크기(x, y) x=가로 y=세로
plot = sns.countplot('name', data=df)      # 그래프 함수 : sns.countplot() 사용

# column 그래프 부가 설명(옵션)
plot.set_title('Chat count of name', fontsize=30)    # 제목
plot.set_xlabel('Name', fontdict={'size':20})        # x축 이름
plot.set_ylabel('Chat count', fontdict={'size':20})  # y축 이름
plt.savefig('Chat_count_of_name.png')                # 이미지로 저장
plt.show()
```

### step 3. wordcloud


```python
text_sum = ''
```


```python
# 한 문장으로 합치기
for i in df['text']:
    text_sum = text_sum + i
text_sum
```


```python
# 자음, 모음, 알파벳, 특수기호, 특수기호 제거
text_sub = re.sub(r'[ㄱ-ㅎㅏ-ㅣa-z]', '', text_sum)
text_sub
```


```python
tokens_ko = t.morphs(text_sub)
tokens_ko
```


```python
import nltk
from konlpy.tag import Okt; t = Okt()
```


```python
ko = nltk.Text(tokens_ko)   
print(len(ko.tokens))          # 토큰 전체 갯수
print(len(set(ko.tokens)))     # 토큰 unique 갯수
```
ko.vocab().most_common(100)

```python
# 불용어 : 인터넷 검색 시 검색 용어로 사용하지 않는 단어. 관사, 전치사, 조사, 접속사 등 검색 색인 단어로 의미가 없는 단어
stop_words = ['.','가',"!",'\r\n\r\n','\r\n','\n','\n ','요','답변','...','을','수','에','질문','제','를','이','도',
                      '좋','1','는','로','으로','2','것','은','다',',','니다','대','들',
                      '2017','들','데','..','의','때','겠','고','게','네요','한','일','할',
                      '10','?','하는','06','주','려고','인데','거','좀','는데','~','ㅎㅎ',
                      '하나','이상','20','뭐','까','있는','잘','습니다','다면','했','주려',
                      '지','있','못','후','중','줄','6','과','어떤','기본','!!',
                      '단어','라고','중요한','합','가요','....','보이','네','무지',
                      'ㅋㅋ', 'ㅋㅋㅋ', 'ㅋ', '만', '아', '안,' '나', '사진', '난', '이모티콘',
                      '내', '그', '근데', '더', '안', '나', '임', '저', '면', '듯', '년', '하면', '에서',
                      '너', '서', '랑', '에서', '니깐', '적', '하고', '??', '~~', '~~~']

tokens_ko = [each_word for each_word in tokens_ko
             if each_word not in stop_words]

ko = nltk.Text(tokens_ko)
ko.vocab().most_common(50)
```


```python
data = ko.vocab().most_common(300)
data
```


```python
from wordcloud import WordCloud, STOPWORDS
from PIL import Image
```


```python
# 워드클라우드를 그려보자
wordcloud = WordCloud(font_path='c:/Windows/Fonts/malgun.ttf',
                      relative_scaling = 0.2,
                      #stopwords=STOPWORDS,
                      background_color='white',
                      ).generate_from_frequencies(dict(data))
plt.figure(figsize=(16,8))
plt.imshow(wordcloud)
plt.axis("off")
plt.show()
```


```python
# 다음과 같이 파일로 저장
wordcloud.to_file('wordcloud.png')
```


```python

```
