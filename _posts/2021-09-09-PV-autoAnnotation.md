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
    * OpenCV 4.5.3
    * python 3.8

* * *
* step0. 원본(original image)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotation.jpg?raw=true)

* step1. b, g, r 분할(Split)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step1.png?raw=true)

* step2. zero 행렬 생성 및 병합(Merge)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step2.png?raw=true)

* step3. 흐림 효과(Blur)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step3.png?raw=true)

* step4. 역상(Reverse Image)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step4.png?raw=true)

* step5. 그레이 스케일(Gray Scale)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step5.png?raw=true)

* step6. 이진화(Binary)
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/annotationRecognition_step6.png?raw=true)

* step7. 윤곽선(Contour)
    * Curve
    ![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/resultAutoAnnotationCurve.png?raw=true)

    * BBox
    ![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/resultAutoAnnotationBbox.png?raw=true)
    
* * *

```python
import cv2
import numpy as np
from matplotlib import pyplot as plt

# 이지미 불러오기
img_bgr = cv2.imread("image/annotation.jpg", cv2.IMREAD_COLOR)
cv2.imshow("img_bgr", img_bgr)
cv2.waitKey()
cv2.destroyAllWindows()

# bgr로 분할
b, g, r = cv2.split(img_bgr)
cv2.imshow("b", b)
cv2.imshow("g", g)
cv2.imshow("r", r)
cv2.waitKey()
cv2.destroyAllWindows()

# 0 행렬 생성 후 merge
z = np.zeros(shape=(b.shape[0], b.shape[1]), dtype="uint8")
img_zgr = cv2.merge((b, r, z))
cv2.imshow("img_zgr", img_zgr)
cv2.waitKey()
cv2.destroyAllWindows()

# 흐림 효과(Blur)
img_blur = cv2.blur(img_zgr, (15, 15), anchor=(-1, -1), borderType=cv2.BORDER_DEFAULT)
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
ret, img_binary = cv2.threshold(img_bitwise_not_bgr2gray, 237,255,cv2.THRESH_BINARY)
cv2.imshow("img_binary", img_binary)
cv2.waitKey()
cv2.destroyAllWindows()

# 윤곽선(Contour)
contours, hierarchy = cv2.findContours(img_binary, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)

# curve
img_contour_curve = img_bgr.copy()
result_cnt=[]
for cnts in contours:
    # 일정 면적 무시
    if cv2.contourArea(cnts) < 500 or cv2.contourArea(cnts) > img_bgr.shape[0] ** 2 * 0.9:
        continue
    approx = cv2.approxPolyDP(cnts, cv2.arcLength(cnts, True)*0.02, True)
    vtc = len(approx)
    # 꼭지점 4개 이상인 경우
    if vtc >= 4:
        img_contour_curve = cv2.drawContours(img_contour_curve, cnts, -1, (0, 255, 0), 2)
        result_cnt.append(cnts)
cv2.imwrite("resultAutoAnnotationCurve.png", img_contour_curve)
cv2.imshow("img_contour_curve", img_contour_curve)
cv2.waitKey()
cv2.destroyAllWindows()

# bbox
img_contour_bbox = img_bgr.copy()
for recnt in result_cnt:
    x,y,w,h = cv2.boundingRect(recnt)
    img_contour_bbox = cv2.rectangle(img_contour_bbox,(x,y),(x+w,y+h),(0,255,0),2)
cv2.imwrite("resultAutoAnnotationBbox.png", img_contour_bbox)
cv2.imshow("img_contour_bbox", img_contour_bbox)
cv2.waitKey()
cv2.destroyAllWindows()
```