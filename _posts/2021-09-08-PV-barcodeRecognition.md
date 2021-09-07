---
layout: post
title: "[Vision] OpenCV - 바코드 인식"
subtitle: "barcodeRecognition"
categories: python
tags: vision
comments: true
---

![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/resultBarcodeRecognition.png?raw=true)

* 환경
    * OpenCV 4.5.0
    * pyzbar 0.1.8
    * python 3.8

* * *

* step1. edge detection<br>
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/barcodeRecognition_step1.png?raw=true)
<br>
* step2. find contours of paper<br>
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/barcodeRecognition_step2.png?raw=true)
<br>
* step3. apply perspective Transform<br>
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/barcodeRecognition_step3.png?raw=true)
<br>
* step4. insert the step3 image and barcode text into the original image<br>
![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/vision/resultBarcodeRecognition.png?raw=true)

* * *

```python
# OpenCV - 바코드 인식
import numpy as np
import cv2
import pyzbar.pyzbar as pyzbar

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
    orig = image.copy() # 이미지 복사
    
    barcodeCnt = len(pyzbar.decode(image)) # 바코드 개수

    rHight = 800.0 / image.shape[0]              # 세로 높이 800으로 맞추기 위해
    dim = (int(image.shape[1] * rHight), 800)    # 세로 높이 800으로 맞추는 비율만큼 가로 길이에 곱함
    image = cv2.resize(image, dim, interpolation = cv2.INTER_AREA)  # 이미지 resize
    
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)  # 이미지의 색공간을 BGR에서 GRAY로 변화
    gray = cv2.GaussianBlur(gray, (3, 3), 0)        # GaussianBlur로 blur 효과 부여(윤곽 검출을 위함)
    edged = cv2.Canny(gray, 75, 200)                # Canny Edge Detection을 통해 edge 검출

    # step2. find contours of paper
    (cnts, _) = cv2.findContours(edged.copy(), cv2.RETR_LIST, cv2.CHAIN_APPROX_SIMPLE) # findContours를 통해 contours들을 반환받음

    cnts = sorted(cnts, key = cv2.contourArea, reverse = True)[:barcodeCnt*2] # 반환 받은 contour를 윤곽이 그린 면적(cv2.contourArea)이 큰 순서대로 정렬해서 barcodeCnt개수 * 2개 받아옴
    
    screenCnts = []
    for i, c in enumerate(cnts): # contour를 순차적으로 탐색
        if i % 2 == 1: # for문 중 홀수일 경우만
            peri = cv2.arcLength(c, True) # contour가 그리는 길이를 반환
            approx = cv2.approxPolyDP(c, 0.02 * peri, True) # 그 길이에 2% 정도 오차를 해서 approxPolyDP를 통해 도형을 근사해서 구함

            if len(approx) == 4:    # 도형을 근사해서 추출한 윤곽이 꼭지점이 4개라면 그것이 명함의 윤곽으로 지정
                screenCnts.append(approx)

    cv2.drawContours(image, screenCnts, -1, (0, 255, 0), 2) # drawContours를 통해 contours를 그림

    # step3. apply perspective Transform
    for screenCnt in screenCnts: # 바코드 개수만큼 for문
        rect = order_points(screenCnt.reshape(4, 2) / rHight) # contours에서 4개의 꼭지점을 4x2의 배열로 재정렬하여 rHight로 나눔 (원본 이미지로 변환하기 위해)
        (topLeft, topRight, bottomRight, bottomLeft) = rect

        w1 = abs(bottomRight[0] - bottomLeft[0])    # 하단 폭
        w2 = abs(topRight[0] - topLeft[0])          # 상단 폭
        h1 = abs(topRight[1] - bottomRight[1])      # 우측 높이
        h2 = abs(topLeft[1] - bottomLeft[1])        # 좌측 높이

        maxWidth = int(max([w1, w2]))    # 최대 폭
        maxHeight = int(max([h1, h2]))   # 최대 높이

        dst = np.float32([[0, 0], [maxWidth, 0], [maxWidth, maxHeight], [0, maxHeight]]) # 변환될 크기만큼 행렬 생성

        M = cv2.getPerspectiveTransform(rect, dst) # getPerspectiveTransform()함수를 통해서 나머지 픽셀을 옮기는 매트릭스 M에 반환
        
        warped = cv2.warpPerspective(orig, M, (maxWidth, maxHeight)) # M을 warpPerspective()에 넣음으로써 최종적으로 반듯한 사각형으로 변환된 이미지를 받음
        
        # step4. insert the step3 image and barcode text into the original image
        xCoor = [x[0][0] for x in screenCnt] # 꼭지점의 x 좌표 리스트
        yCoor = [y[0][1] for y in screenCnt] # 꼭지점 y 좌표 리스트
        xMin = int(min(xCoor)/rHight) # x 최소값
        xMax = int(max(xCoor)/rHight) # x 최대값
        yMin = int(min(yCoor)/rHight) # y 최소값
        yMax = int(max(yCoor)/rHight) # y 최대값
        warped = cv2.resize(warped, (xMax-xMin, yMax-yMin), interpolation = cv2.INTER_AREA)  # 이미지 resize
        orig[yMin:yMax, xMin:xMax] = warped # 정렬한 이미지를 원본에 붙여넣기 (각 위치별 x, y의 최소값 기준)

        decodedObjects = pyzbar.decode(warped) # 바코드 탐지
        orig = cv2.putText(orig, str(decodedObjects[0].data), (xMin, yMax+50), cv2.FONT_HERSHEY_COMPLEX, 2, (0, 255, 255), 3) # 디코드 글자 삽입

    print("barcode number:", len(screenCnts)) # 바코드 탐지 개수 프린트
    cv2.imwrite("resultBarcodeRecognition.png", orig) # 결과 저장


if __name__ == "__main__":
    auto_scan_image("image/barcode.jpg")
```