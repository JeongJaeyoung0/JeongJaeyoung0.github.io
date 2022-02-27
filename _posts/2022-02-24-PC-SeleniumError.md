---
layout: post
title: "[Crawling] SeleniumError"
subtitle: "Instagram"
categories: python
tags: crawling
comments: true
---

# selenium 3.x version
본 글 이전에 작성한 크롤링은 `selenium 3.x` 버전에서 작동하는 코드다.

selenium 4.x 버전에서 아래 코드를 실행하면,
``` python
webdriver.Chrome(r"./chromedriver.exe")
```

아래와 같은 에러를 발생 시킨다. (mac 기준)
```
WebDriverException: Message: Service ./chromedriver unexpectedly exited. Status code was: -9
```

따라서, 정상 작동하기 위해 아래와 같이 selenium을 3.x로 설치할 필요가 있다.

``` python
pip install selenium==3.14.0
```

* * *

# selenium 4.x version
`selenium 4.x` 버전은 크롬 버전이 업데이트 됨에 따라 chromdrive도 업데이트 해줘야 하는 단점이 잡힌듯 하다. (직접 확인해보진 않았다.)