---
layout: post
title: "[Vision] OpenCV - 명함 인식"
subtitle: "cardRecognition"
categories: python
tags: vision
comments: true
---

![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/cardRecognition.png?raw=true)

* 환경
    * OpenCV 4.5.3
    * python 3.8

* * *
* step0. original image
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/card.png?raw=true)

* step1. edge detection
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/cardRecognition_step1-2.png?raw=true)

* step2. find contours of paper
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/cardRecognition_step2.png?raw=true)

* step3. apply perspective Transform
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/cardRecognition_step3.png?raw=true)

* step4. apply adaptive threshold
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/cardRecognition_step4.png?raw=true)

* * *

```python
# OpenCV - 명함인식
import numpy as np
import cv2

def order_points(pts):
    rect = np.zeros((4, 2), dtype = "float32") # 4개 꼭지점 좌표 입력할 4x2 행렬 생성

    s = pts.sum(axis = 1)       # (x, y) 좌표에서 x+y 계산 (axis 0=열, 1=행)
    rect[0] = pts[np.argmin(s)] # x+y의 최대값 (topLeft)
    rect[2] = pts[np.argmax(s)] # x+y의 최소값 (bottomRight)

    diff = np.diff(pts, axis = 1)  # (x, y) 좌표에서 y-x 계산 (axis 0=열, 1=행)
    rect[1] = pts[np.argmin(diff)] # y-x의 최소값 (topRight)
    rect[3] = pts[np.argmax(diff)] # y-x의 최대값 (bottomLeft)
    return rect

def auto_scan_image(dir):
    # step1. edge detection
    image = cv2.imread(dir) # 이미지 읽기
    orig = image.copy()     # 이미지 복사

    rHight = 800.0 / image.shape[0]              # 세로 높이 800으로 맞추기 위해
    dim = (int(image.shape[1] * rHight), 800)    # 세로 높이 800으로 맞추는 비율만큼 가로 길이에 곱함
    image = cv2.resize(image, dim, interpolation = cv2.INTER_AREA)  # 이미지 resize

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)  # 이미지의 색공간을 BGR에서 GRAY로 변화
    gray = cv2.GaussianBlur(gray, (3, 3), 0)        # GaussianBlur로 blur 효과 부여(윤곽 검출을 위함)
    edged = cv2.Canny(gray, 75, 200)                # Canny Edge Detection을 통해 edge 검출

    print("step1. edge detection")
    cv2.imshow("Image", image)
    cv2.imshow("Edged", edged)
    cv2.waitKey()
    cv2.destroyAllWindows()

    # step2. find contours of paper
    (cnts, _) = cv2.findContours(edged.copy(), cv2.RETR_LIST, cv2.CHAIN_APPROX_SIMPLE) # findContours를 통해 contours들을 반환받음

    cnts = sorted(cnts, key = cv2.contourArea, reverse = True)[:5] # 반환 받은 contour를 윤곽이 그린 면적(cv2.contourArea)이 큰 순서대로 정렬해서 5개만 받아옴

    for c in cnts: # contour를 순차적으로 탐색
        peri = cv2.arcLength(c, True) # contour가 그리는 길이를 반환
        approx = cv2.approxPolyDP(c, 0.02 * peri, True) # 그 길이에 2% 정도 오차를 해서 approxPolyDP를 통해 도형을 근사해서 구함

        if len(approx) == 4:    # 도형을 근사해서 추출한 윤곽이 꼭지점이 4개라면 그것이 명함의 윤곽으로 지정
            screenCnt = approx
            break

    print("step2. find contours of paper")
    cv2.drawContours(image, [screenCnt], -1, (0, 255, 0), 2) # drawContours를 통해 contours를 그림
    cv2.imshow("Outline", image)
    cv2.waitKey()
    cv2.destroyAllWindows()

    # step3. apply perspective Transform
    rect = order_points(screenCnt.reshape(4, 2) / rHight) # contours에서 4개의 꼭지점을 4x2의 배열로 재정렬하여 rHight로 나눔
    (topLeft, topRight, bottomRight, bottomLeft) = rect

    w1 = int(abs(bottomRight[0] - bottomLeft[0]))    # 하단 폭
    w2 = int(abs(topRight[0] - topLeft[0]))          # 상단 폭
    h1 = int(abs(topRight[1] - bottomRight[1]))      # 우측 높이
    h2 = int(abs(topLeft[1] - bottomLeft[1]))        # 좌측 높이

    maxWidth = max([w1, w2])    # 최대 폭
    maxHeight = max([h1, h2])   # 최대 높이

    dst = np.float32([[0, 0], [maxWidth-1, 0], [maxWidth-1, maxHeight-1], [0, maxHeight-1]]) # 변환될 크기만큼 행렬 생성 (1씩 작게)

    M = cv2.getPerspectiveTransform(rect, dst) # getPerspectiveTransform()함수를 통해서 나머지 픽셀을 옮기는 매트릭스 M에 반환

    warped = cv2.warpPerspective(orig, M, (maxWidth, maxHeight)) # M을 warpPerspective()에 넣음으로써 최종적으로 반듯한 사각형으로 변환된 이미지를 받음

    print("step3. apply perspective Transform")
    cv2.imshow("Warped", warped)
    cv2.waitKey()
    cv2.destroyAllWindows()

    # step4. apply adaptive threshold
    warped = cv2.cvtColor(warped, cv2.COLOR_BGR2GRAY)
    warped = cv2.adaptiveThreshold(warped, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 21, 10) # adaptiveThresholde()를 통해서 흑백으로 바꿈

    print("step4. apply adaptive threshold")
    cv2.imshow("Original", orig)
    cv2.imshow("Scanned", warped)
    cv2.imwrite("resultCardRecognition.png", warped)
    cv2.waitKey()
    cv2.destroyAllWindows()

if __name__ == "__main__":
    auto_scan_image("image/card.png")
```