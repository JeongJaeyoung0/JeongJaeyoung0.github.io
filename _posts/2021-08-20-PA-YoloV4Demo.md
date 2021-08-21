---
layout: post
title: "[AI] 비전 - Yolo V4 데모, pb, h5"
subtitle: "YoloV4Demo"
categories: python
tags: ai
comments: true
---

![image]()

* 목적: image bounding box, label, confidence, convert to pb, h5

* 환경
    * Ubuntu 18.04
    * Tensorflow 2.3.0rc0

<br>

### 1. 가상환경 설정
```python
conda create -n yolov4 pip python=3.7 
conda activate yolov4
```

### 2. yolov4 clone
```python
git clone https://github.com/JeongJaeyoung0/tensorflow-yolov4
```

### 3. tensorflow-yolov4 폴더로 디렉토리 변경
```python
cd tensorflow-yolov4
```

### 4. 패키지 설치 (gpu, cpu 둘중 하나 설치)
```python
# gpu 버전
pip install -r requirements-gpu.txt

# cpu 버전
pip install -r requirements.txt
```

### 5. [링크](https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.weights) 클릭하여 다크넷에서 제공하는 데모 yolov4.weights 다운로드

### 6. 4번에서 다운 받은 yolov4.weights를 tensorflow-yolov4/data로 이동

### 7. 데모
```python
# yolov4
python detect.py --weights ./data/yolov4.weights --framework tf --size 608 --image ./data/kite.jpg --output result.png
```

### 8. Convert
```python
# .weights to .pb (tensorflow)
python convert.py --weights ./data/yolov4.weights --output ./data/yolov4-pb

# .weights to .h5 (keras)
python convert.py --weights ./data/yolov4.weights --output ./data/yolov4.h5
```
