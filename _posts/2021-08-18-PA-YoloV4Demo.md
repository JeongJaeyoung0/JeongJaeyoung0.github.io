---
layout: post
title: "[AI] 비전 - Yolo V4 데모"
subtitle: "YoloV4Demo"
categories: python
tags: ai
comments: true
---

![image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/ai/kite.png?raw=true)

* 목적: image bounding box, label, confidence

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
git clone https://github.com/JeongJaeyoung0/tensorflow-yolov4-tflite.git
```

### 3. tensorflow-yolov4-tflite 폴더로 디렉토리 변경
```python
cd tensorflow-yolov4-tflite
```

### 4. 패키지 설치 (gpu, cpu 둘중 하나 설치)
 * `gpu` 버전
```python
pip install -r requirements-gpu.txt
```
 * `cpu` 버전
```python
pip install -r requirements.txt
```

### 5. [링크](https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.weights) 클릭하여 다크넷에서 제공하는 데모 yolov4.weights 다운로드

### 6. 4번에서 다운 받은 yolov4.weights를 tensorflow-yolov4-tflite/data에 이동

### 7. darknet가중치 파일을 tensorflow 버전으로 변환
 * `일반` 버전
```python
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416 --input_size 416 --model yolov4
```

 * `Lite` 버전
```python
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416-tflite --input_size 416 --model yolov4 --framework tflite
python convert_tflite.py --weights ./checkpoints/yolov4-416-tflite --output ./checkpoints/yolov4-416.tflite
```
### 8. 데모 - Yolo v4 (PC에선 일반 버전이 더 빠름)
 * `일반` 버전
```python
python detect.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --image ./data/kite.jpg
```
결과물: 현재 디렉토리에 result.png<br>
다른 사진: kite.jpg를 변경

 * `Lite` 버전
```python
python detect.py --weights ./checkpoints/yolov4-416.tflite --size 416 --model yolov4 --image ./data/kite.jpg --framework tflite
```

 * `video`
```python
python detectvideo.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --video ./data/road.mp4
```

<br>

환경에 따라 에러가 다소 발생하지만, 에러 내용을 구글링 하면 쉽게 해결 가능하다.