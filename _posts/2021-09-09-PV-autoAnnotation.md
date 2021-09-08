---
layout: post
title: "[Vision] OpenCV - 윤곽선 검출"
subtitle: "autoAnnotation"
categories: python
tags: vision
comments: true
---

![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/resultAutoAnnotation.png?raw=true)

* 환경
    * OpenCV 4.5.0
    * python 3.8

의도한 형태의 검출은 아니지만, 변수를 조정하면 좀더 정밀한 검출이 가능 할 듯 하다. 현재는 이미지의 전체 윤곽도 검출되지만, 좀더 개선해 보려 한다.
* * *
* step0. 원본(original image)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotation.jpg?raw=true)

* step1. 흐림 효과(Blur)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step1.png?raw=true)

* step2. 역상(Reverse Image)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step2.png?raw=true)

* step3. 그레이 스케일(Gray Scale)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step3.png?raw=true)

* step4. 이진화(Binary)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step4.png?raw=true)

* step5. 윤곽선(Contour)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/resultAutoAnnotation.png?raw=true)

* * *

```python
import cv2
from matplotlib import pyplot as plt

img_bgr = cv2.imread('image/annotation.jpg')
cv2.imshow("img_bgr", img_bgr)
cv2.waitKey()
cv2.destroyAllWindows()

# 흐림 효과(Blur)
img_blur = cv2.blur(img_bgr, (10, 10), anchor=(-1, -1), borderType=cv2.BORDER_DEFAULT)
#cv2.bilateralFilter(imgray,15,20,20)
cv2.imshow("img_blur", img_blur)
cv2.waitKey()
cv2.destroyAllWindows()

# 역상(Reverse Image)
img_bitwise_not_bgr = cv2.bitwise_not(img_blur)
cv2.imshow("img_bitwise_not_bgr", img_bitwise_not_bgr)
cv2.waitKey()
cv2.destroyAllWindows()

# 그레이 스케일(Gray Scale)
img_bitwise_not_bgr2gray = cv2.cvtColor(img_bitwise_not_bgr, cv2.COLOR_BGR2GRAY)
cv2.imshow("img_bitwise_not_bgr2gray", img_bitwise_not_bgr2gray)
cv2.waitKey()
cv2.destroyAllWindows()

# 이진화(Binary)
ret, img_binary = cv2.threshold(img_bitwise_not_bgr2gray, 220,230,cv2.THRESH_BINARY)
cv2.imshow("img_binary", img_binary)
cv2.waitKey()
cv2.destroyAllWindows()

# 윤곽선(Contour)
contours, hierarchy = cv2.findContours(img_binary, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)
# 1번째 인수(argument)값 img_bgr는 원본 이미지를 의미.
# 4번째 인수(argument)값 (0, 255, 0)는 R,G,B를 의미. 녹색(Green)값 255의 윤곽선
# 5번째 인수(argument)값 2는 윤곽선의 굵기를 의미
img_contour = cv2.drawContours(img_bgr, contours, -1, (0, 255, 0), 2)
cv2.imwrite("resultAutoAnnotation.png", img_contour)
cv2.imshow("img_contour", img_contour)
cv2.waitKey()
cv2.destroyAllWindows()
```