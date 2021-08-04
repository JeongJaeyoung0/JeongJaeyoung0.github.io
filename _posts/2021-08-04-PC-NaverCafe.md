---
layout: post
title: "[Crawling] Naver Cafe"
subtitle: "NaverCafe"
categories: python
tags: crawling
comments: true
---

* 수집: 게시판 글 목록
* 코딩: [github](https://github.com/JeongJaeyoung0/crawling/blob/ec5b6b7b9380fc3dac5f83ebf0b284aecd796ad5/crawling_naver_cafe_%EA%B2%8C%EC%8B%9C%ED%8C%90_%EA%B8%80_%EB%AA%A9%EB%A1%9D.ipynb "github")

<br>

# ● code

***

# crawling_naver cafe_게시판 글 목록
Step 1. 네이버 카페 > 게시판 > 글번호, 제목, 작성자, 좋아요 수집 > 저장 (crawler_naver cafe_게시판 {}.xlsx)공지 숨겨도 크롤링에 포함됨
공지 숨기기 클릭
anno_off = driver.find_element_by_css_selector('.check_box').click()
### Step 0. 준비


```python
import sys    # 시스템
import os     # 시스템

import pandas as pd    # 판다스 : 데이터분석 라이브러리
import numpy as np     # 넘파이 : 숫자, 행렬 데이터 라이브러리

from bs4 import BeautifulSoup     # html 데이터 전처리
from selenium import webdriver    # 웹 브라우저 자동화
import time                       # 시간 지연
import math
```

### Step 1. 크롤링


```python
keyword = "☰ 통합 Q & A ☰"
crawling_no = int(input('클롤링 할 글 개수를 입력 :'))
```

    클롤링 할 글 개수를 입력 :10
    


```python
# 크롬 웹브라우저 실행
driver = webdriver.Chrome(r"./chromedriver/chromedriver.exe")

# 사이트 주소
driver.get("https://cafe.naver.com/noljatravel")
time.sleep(2)

# 게시판 클릭
driver.find_element_by_link_text(keyword).click()

# 게시판 프레임 접근
driver.switch_to.frame("cafe_main")

# 게시글 50개씩
driver.find_element_by_css_selector("#listSizeSelectDiv").click()
driver.find_element_by_xpath("/html/body/div[1]/div/div[3]/div/div[3]/ul/li[7]/a").click()
```


```python
#crawling_list = []
no_app = []
title_app = []
nick_app  = []
like_app  = []

# 크롤링 해야 할 페이지 계산
crawling_page = int(math.ceil(crawling_no / 50)+1)

try: 
    for page in range(1,crawling_page):
        # 페이지 클릭
        driver.find_element_by_link_text(str(page)).click()
        time.sleep(1)
        # 글 번호 수집
        no = [i.text for i in driver.find_elements_by_css_selector('.td_article')]
        no_split = [ni.split()[0] for ni in no]
        # 글 제목 수집
        title = [i.text for i in driver.find_elements_by_css_selector('.article')]
        # 작성자 수집
        nick = [i.text for i in driver.find_elements_by_css_selector('.p-nick .m-tcol-c')]
        # 좋아요 수집
        like = [i.text for i in driver.find_elements_by_css_selector('.td_likes')]
        # 수집 데이터 append
        no_app.append(no_split)
        title_app.append(title)
        nick_app.append(nick)
        like_app.append(like)
        # 10페이지 마다 프린트 & 다음 페이지로 클릭
        if str(page)[-1] == '0':
            print(int(page), 'page 크롤링 완료')
            driver.find_element_by_link_text('다음').click()
# 더이상 페이지가 존재하지 않을 시
except:
    print('더이상 페이지가 존재하지 않음')

driver.close()
    
# 리스트안 리스트 분해
no_list = sum(no_app, [])
title_list = sum(title_app, [])
nick_list = sum(nick_app, [])
like_list = sum(like_app, [])

# 판다스화
df = pd.DataFrame({'번호':no_list,
                   '제목':title_list,
                   '작성자':nick_list,
                   '좋아요':like_list})
# 필독, 공지 삭제
df = df.drop(df[df['번호'] == '필독'].index)
df = df.drop(df[df['번호'] == '공지'].index)
df = df.reset_index(drop=True)

print('글 ', len(df), '개 크롤링 완료. \n크롤링 종료.', sep='')
```

    글 50개 크롤링 완료. 
    크롤링 종료.
    


```python
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
      <th>번호</th>
      <th>제목</th>
      <th>작성자</th>
      <th>좋아요</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>327461</td>
      <td>블박 ssd 로 저장하시는 분들은 오류가 없나요?</td>
      <td>세종T뚝딱망치</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>327460</td>
      <td>P &gt; D, D &gt; P 변경 시 외부 소음이 어느정도 들리시나요?</td>
      <td>송파구T내무부장관</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>327448</td>
      <td>넷플릭스</td>
      <td>부산T대저촌놈</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>327431</td>
      <td>[충전기질문] 단독주택 집밥 완속충전기 설치 하신분?</td>
      <td>서울T화야</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>327423</td>
      <td>[충전질문] 충전 매일매일 하면 안좋은게 있나요?</td>
      <td>경기파주T쭌압바</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>327418</td>
      <td>[AS질문] 핸들 조향 시 소음이 나네요.</td>
      <td>춘천T모3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>327393</td>
      <td>분명 하차시에 그냥 280킬로였는데</td>
      <td>인천T사고쟁이</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>327371</td>
      <td>[집밥질문] 부산 사시는분들 집밥 문의 드려요.</td>
      <td>울산T화랑</td>
      <td>0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>327363</td>
      <td>도와주세요) 충전기 설치 건의 거부.</td>
      <td>서울T이가</td>
      <td>0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>327353</td>
      <td>[충전질문] 저희 아파트 집밥 가능한 충전기인가요??</td>
      <td>강원T팡팡팡이</td>
      <td>0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>327336</td>
      <td>폰키를 주키로 사용하고, 차 안에 카드키를 두고 다니면 도어 개폐에 영향이 갈까요??</td>
      <td>서울T옥동자</td>
      <td>0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>327329</td>
      <td>[AS질문] 혹시 성수서비스센터 근처에 갈만한곳 추천?</td>
      <td>경대T폴겟폴갓</td>
      <td>0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>327319</td>
      <td>[가격질문] 전기차 보험 문의</td>
      <td>경남T꼬레아</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>327318</td>
      <td>[기능질문] 프리미엄 커넥티비티 끝난후 라우터 사용시 원격 차량 접속</td>
      <td>수원T궁둥이오리</td>
      <td>0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>327312</td>
      <td>퍼포먼스 모델3 입니다.ps4s 타이어위치교환</td>
      <td>대구T씨티보이</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>327307</td>
      <td>화훼이 도착 했습니다 ㅎ</td>
      <td>인천T사고쟁이</td>
      <td>0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>327305</td>
      <td>딥블루 화이트시트 19휠</td>
      <td>구미T테슬라이프</td>
      <td>0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>327246</td>
      <td>중고차 판매 관련...</td>
      <td>동탄T쿠링</td>
      <td>0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>327228</td>
      <td>충전방식 문의</td>
      <td>대구T우</td>
      <td>0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>327219</td>
      <td>모델Y 오토프렁크 했는데... 선 하나가 남아요ㅠ</td>
      <td>충주T날믿어줘</td>
      <td>2</td>
    </tr>
    <tr>
      <th>20</th>
      <td>327213</td>
      <td>모3롱 왕복 330km정도 거리 여행 괜찮을까요?</td>
      <td>대구T홀이</td>
      <td>1</td>
    </tr>
    <tr>
      <th>21</th>
      <td>327156</td>
      <td>[사고질문] 접촉 사고가 발생했습니다</td>
      <td>강남구T욱</td>
      <td>2</td>
    </tr>
    <tr>
      <th>22</th>
      <td>327155</td>
      <td>다나와 캐시백이랑 카페 할부 동시에 이용 가능한가요?</td>
      <td>수원T킴돔</td>
      <td>0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>327146</td>
      <td>한달 200-230kw 사용 시 이동형파워큐브 의미 없겠죠?</td>
      <td>부산T하이</td>
      <td>0</td>
    </tr>
    <tr>
      <th>24</th>
      <td>327129</td>
      <td>대전 에어컨 필터 교체..</td>
      <td>대전T별명</td>
      <td>0</td>
    </tr>
    <tr>
      <th>25</th>
      <td>327114</td>
      <td>모델3 주차타워 주차해도 되나요?</td>
      <td>청도T간백</td>
      <td>0</td>
    </tr>
    <tr>
      <th>26</th>
      <td>327105</td>
      <td>전기차운행후.왼쪽무릎통증</td>
      <td>대구T오겹살</td>
      <td>0</td>
    </tr>
    <tr>
      <th>27</th>
      <td>327102</td>
      <td>헤이딜러 이용해보신분</td>
      <td>분당T운칠기삼</td>
      <td>1</td>
    </tr>
    <tr>
      <th>28</th>
      <td>327101</td>
      <td>보조금 자격 부여?</td>
      <td>고양T테설라</td>
      <td>1</td>
    </tr>
    <tr>
      <th>29</th>
      <td>327099</td>
      <td>신차 검수 어떻게 하시나요?</td>
      <td>경기T슈퍼소닉</td>
      <td>0</td>
    </tr>
    <tr>
      <th>30</th>
      <td>327097</td>
      <td>완속충전기 설치된 팬션 등에 충전 속도가 어느 정도인가요?</td>
      <td>세종T밀크쉐이크</td>
      <td>0</td>
    </tr>
    <tr>
      <th>31</th>
      <td>327093</td>
      <td>5월말 모3롱 주문은 언제쯤 연락올까요?</td>
      <td>인천T동네형아</td>
      <td>0</td>
    </tr>
    <tr>
      <th>32</th>
      <td>327083</td>
      <td>[인벤질문] 옵션 변경시 순번영향 없겠죠?</td>
      <td>구리T더콩</td>
      <td>0</td>
    </tr>
    <tr>
      <th>33</th>
      <td>327082</td>
      <td>한쇼계기판 구글 서비스 에러 어떻게 해결 하나요?</td>
      <td>아산T동백꽃단주</td>
      <td>0</td>
    </tr>
    <tr>
      <th>34</th>
      <td>327078</td>
      <td>모델3 퍼포먼스</td>
      <td>서울T J</td>
      <td>0</td>
    </tr>
    <tr>
      <th>35</th>
      <td>327077</td>
      <td>모3 퍼포 재고들 이 여름 더위에 야적이었겠죠?</td>
      <td>서울T일리네어</td>
      <td>1</td>
    </tr>
    <tr>
      <th>36</th>
      <td>327076</td>
      <td>[가격질문] fsd 취소</td>
      <td>경기T윤주아빠</td>
      <td>0</td>
    </tr>
    <tr>
      <th>37</th>
      <td>327058</td>
      <td>배터리 사용시</td>
      <td>김포T노가다</td>
      <td>0</td>
    </tr>
    <tr>
      <th>38</th>
      <td>327057</td>
      <td>셀프 차량등록 질문</td>
      <td>경기T새들맨</td>
      <td>0</td>
    </tr>
    <tr>
      <th>39</th>
      <td>327052</td>
      <td>M3L 이제 조금 있으면 출고 인데...틴팅 농도 문의 드립니다.</td>
      <td>동탄T쿠링</td>
      <td>0</td>
    </tr>
    <tr>
      <th>40</th>
      <td>327048</td>
      <td>사고나신분들 처리기간이랑 어떻게 처리하셨어요?</td>
      <td>세종T내옹</td>
      <td>0</td>
    </tr>
    <tr>
      <th>41</th>
      <td>327020</td>
      <td>출고시 배터리 풀충전돼서 출고되나요?</td>
      <td>분당T운칠기삼</td>
      <td>1</td>
    </tr>
    <tr>
      <th>42</th>
      <td>327018</td>
      <td>[기능질문] 센트리모드 저장용과 음악용 SSD 따로 사용가능한가요?</td>
      <td>창원T나쁜유령</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43</th>
      <td>327010</td>
      <td>생애 첫차 보조금 질문입니다</td>
      <td>경기T신강유</td>
      <td>1</td>
    </tr>
    <tr>
      <th>44</th>
      <td>326997</td>
      <td>[계약질문] 견적 문의드립니다. 보증금이 차값보다 큰경우</td>
      <td>청주T전차</td>
      <td>1</td>
    </tr>
    <tr>
      <th>45</th>
      <td>326994</td>
      <td>퍼포먼스 타이어 교체 문의 드립니다!!</td>
      <td>광주T볼트EV</td>
      <td>0</td>
    </tr>
    <tr>
      <th>46</th>
      <td>326985</td>
      <td>[계약질문] 법인명의 캐피탈결제 관련 자문좀구하고싶습니다</td>
      <td>수원T이켄</td>
      <td>1</td>
    </tr>
    <tr>
      <th>47</th>
      <td>326976</td>
      <td>[사고질문] 18인치 휠 사고 처리방법</td>
      <td>수원T재원</td>
      <td>0</td>
    </tr>
    <tr>
      <th>48</th>
      <td>326973</td>
      <td>watch app for tesla에서 summon이 될까요?</td>
      <td>화성T모텔3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>49</th>
      <td>326961</td>
      <td>보조금없이 출고한 후</td>
      <td>서울T전기쟁이</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 저장
df.to_excel('crawler_naver cafe_게시판 {}.xlsx'.format(keyword))
```


```python

```
