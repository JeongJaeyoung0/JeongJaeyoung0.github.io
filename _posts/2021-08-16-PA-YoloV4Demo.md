---
layout: post
title: "[AI] 비전 - Yolo V4 데모"
subtitle: "YoloV4Demo"
categories: python
tags: ai
comments: true
---

* 환경
    * Ubuntu 18.04
    * Python 3.7

<br>

1. 가상환경 설정

```python
conda create -n py37 pip python=3.7 
conda activate py37
```

2. 패키지 설치

```python
pip install tensorflow-gpu==2.3.0rc0
pip install opencv-python
pip install easydict
pip install pillow
```

3. yolov4 clone

```python
git clone https://github.com/hunglc007/tensorflow-yolov4-tflite
```

4. [링크](https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.weights) 클릭하여 다크넷에서 제공하는 yolov4.weights 다운로드

5. 4번에서 다운 받은 yolov4.weights 파일을 tensorflow-yolov4-tflite-master\data에 이동

6. core/utils.py 파일 중 152, 159, 161번 줄 수정

```
Line 152 -> c1, c2 = (int(coor[1]), int(coor[0])), (int(coor[3]), int(coor[2]))

Line 159 -> cv2.rectangle(image, c1, (int(np.float32(c3[0])), int(np.float32(c3[1]))), bbox_color, -1)

Line 161 -> cv2.putText(image, bbox_mess, (c1[0], int(np.float32(c1[1] - 2))), cv2.FONT_HERSHEY_SIMPLEX,
fontScale, (0, 0, 0), bbox_thick // 2, lineType=cv2.LINE_AA)
```

7. tensorflow-yolov4-tflite-master 폴더로 디렉토리 변경

```python
cd tensorflow-yolov4-tflite-master
```

8-1. darknet가중치 파일을 tensorflow 버전으로 변환

```python
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416 --input_size 416 --model yolov4
```

8-2. darknet가중치 파일을 tensorflowLite 버전으로 변환

```python
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416-tflite --input_size 416 --model yolov4 --framework tflite
python convert_tflite.py --weights ./checkpoints/yolov4-416-tflite --output ./checkpoints/yolov4-416.tflite
```

9-1. 데모 - Yolo v4 일반 버전 (PC에선 일반 버전이 더 빠름)

```python
ython detect.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --image ./data/kite.jpg
```

9-2. 데모 -  Yolo v4 Lite 버전

```python
python detect.py --weights ./checkpoints/yolov4-416.tflite --size 416 --model yolov4 --image ./data/kite.jpg --framework tflite
```

9-3. 데모 - 비디오

```python
python detectvideo.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --video ./data/road.mp4
```