---
layout: post
title: "[Vision] OpenCV - 명함 인식"
subtitle: "cardRecognition"
categories: python
tags: vision
comments: true
---


* step1.  

<br>

* Encoding (image to base64)

```python
import base64
img = open("/경로/이미지파일.jpg", "rb")
imgToBase64 = base64.b64encode(img.read()).decode("utf8")
img.close()
```

* Encoding된 Base64를 txt로 저장

```python
f = open("base64_result.txt",'w')
f.write(imgToBase64)
f.close()
```

* Decoding (Base64로 된 txt파일 읽어서 이미지로 변환)

```python
from PIL import Image
import base64
import io
fBase64 = open("base64_result.txt", "rb")
line = fBase64.readline()
fBase64.close()
base64ToImg = Image.open(io.BytesIO(base64.b64decode(line)))

# 이미지 리사이즈
resize_img = base64ToImg.resize((416,416))

# 이미지 저장
import cv2
import numpy as np
image = cv2.cvtColor(np.array(resize_img), cv2.COLOR_BGR2RGB)
cv2.imwrite("base64ToImg.png", image)
```