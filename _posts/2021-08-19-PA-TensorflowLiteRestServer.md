---
layout: post
title: "[AI] 비전 - Tensorfllow lite rest server"
subtitle: "TensorflowLiteRestServer"
categories: python
tags: ai
comments: true
---

* 목적: image 입력 → rest server → tflite → return

* 환경
    * Ubuntu 18.04
    * python 3.7

<br>

### 1. 가상환경 설정
```python
conda create -n rest pip python=3.7 
conda activate rest
```

### 2. tensorflow-lite-rest-server clone
```python
git clone https://github.com/robmarkcole/tensorflow-lite-rest-server.git
```

### 3. tensorflow-lite-rest-server 폴더로 디렉토리 변경
```python
cd tensorflow-lite-rest-server
```

### 4. 패키지 설치
 * Linux (x86-64), python 3.7 기준
```python
pip install https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp37-cp37m-linux_x86_64.whl
pip install -r requirements.txt
```
※ os가 다르거나, python 버전이 다르면 [링크](https://www.tensorflow.org/lite/guide/python?hl=ko) 필요한 URL로 install 할 것.

<br>

### 5. 포트 5000에서 tflite-server를 시작
```python
uvicorn tflite-server:app --reload --port 5000 --host 0.0.0.0
```

### 6. cURL을 통해 감시 대상에 이미지 게시
```python
curl -X POST "http://localhost:5000/v1/vision/detection" -H  "accept: application/json" -H  "Content-Type: multipart/form-data" -F "image=@tests/dog.jpg;type=image/jpeg"
```

위 명령어 실행 시 아래 return 출력
```python
{
    "predictions":[
        {
            "label":"dog",
            "confidence":0.93359375,
            "y_min":42,
            "x_min":36,
            "y_max":268,
            "x_max":254
        }],
"success":true}
```

<br>

환경에 따라 에러가 다소 발생하지만, 에러 내용을 구글링 하면 쉽게 해결 가능하다.