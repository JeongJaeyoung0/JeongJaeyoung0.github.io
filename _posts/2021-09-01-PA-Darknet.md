---
layout: post
title: "[AI] 비전 - Darknet custom 학습"
subtitle: "Darknet"
categories: python
tags: ai
comments: true
---

![Image](https://github.com/JeongJaeyoung0/JeongJaeyoung0.github.io/blob/master/assets/img/ai/Sign.png?raw=true)

* 목적
    * custom 학습하기 (결과물: .weights)
* 환경
    * Ubuntu 18.04

<br>

### 1. darknet 다운로드
```python
git clone https://github.com/AlexeyAB/darknet.git
```

### 2. darknet 폴더로 디렉토리 변경
```python
cd darknet
```

### 3. 아래 폴더 트리와같이 custom 폴더 및 파일 생성
```
darknet
└──custom
    ├── custom.data
    ├── custom.names
    ├── custom_images_dir.py
    ├── custom_train.txt
    ├── custom_valid.txt
    ├── images
    │   ├── train
    │   │   ├── CrosswalkSign_00001.jpg
    │   │   ├── CrosswalkSign_00001.txt
    │   │   ├── CrosswalkSign_00002.jpg
    │   │   ├── CrosswalkSign_00002.txt
    │   │   ├── UTurnSign_00001.jpg
    │   │   ├── UTurnSign_00001.txt
    │   │   ├── UTurnSign_00002.jpg
    │   │   └── UTurnSign_00002.txt
    │   └── valid
    │       ├── CrosswalkSign_00003.jpg
    │       ├── CrosswalkSign_00003.text
    │       ├── UTurnSign_00003.jpg
    │       └── UTurnSign_00003.txt
    └── yolov4.cfg
```

* 학습할 image(jpg, png, 등), annotation(txt) 파일을 custom/images/train, valid에 복사
    - annotation txt 파일은 [링크](https://jeongjaeyoung0.github.io/python/2021/08/12/PA-02_Annotation/) 참조하여 생성
<br>
* `custom_images_dir.py`
    - custom_train.txt 생성
    - custom_valid.txt 생성
    - 경로, 이미지 확장자 등 수정할것 (가급적 전체경로 입력하는 것을 추천)
    - 수정 후 아래 코드 실행 시 custom_train.txt, custom_valid.txt 파일이 생성됨
    - 예)
        ```python
        import glob

        # train 이미지 경로.txt 생성
        # 대상 폴더
        image_directory = "/home/shaula/darknet/custom/images/train/"
        # 확장자
        extension = "*.jpg"
        # 텍스트 파일이 저장될 경로
        save_at = "/home/shaula/darknet/custom/custom_train.txt"
        # 대상 폴더에서 지정한 확장자를 가진 파일들의 경로를 리스트화
        files = sorted(glob.glob(image_directory + extension))
        # 파일들의 경로를 텍스트 파일에 추가 및 출력
        for file in files:
            f = open(save_at, 'a')
            f.write(file + "\n")
            print(file)

        # vaild 이미지 경로.txt 생성
        # 대상 폴더
        image_directory = "/home/shaula/darknet/custom/images/valid/"
        # 확장자
        extension = "*.jpg"
        # 텍스트 파일이 저장될 경로
        save_at = "/home/shaula/darknet/custom/custom_valid.txt"
        # 대상 폴더에서 지정한 확장자를 가진 파일들의 경로를 리스트화
        files = sorted(glob.glob(image_directory + extension))
        # 파일들의 경로를 텍스트 파일에 추가 및 출력
        for file in files:
            f = open(save_at, 'a')
            f.write(file + "\n")
            print(file)
        ```

* `custom.data`
    - classes: 분류할 클래스 개수
    - train: 학습할 이미지의 경로가 적힌 txt파일의 경로
    - valid: 검증할 이미지의 경로가 적힌 txt파일의 경로
    - names: .names 파일 경로
    - 예)
        ```python
        classes = 2
        train = custom/custom_train.txt
        valid = custom/custom_valid.txt
        names = custom/custom.names
        backup = backup/
        ```

* `custom.names`
    - 검출하고자 하는 목록 (Annotation txt 파일의 클래스 순서대로 입력)
    - 예)
        ```python
        CrosswalkSign
        UturnSign
        ```

* `yolov4.cfg`
    - darknet/cfg/yolov4.cfg를 복사
    - batch: 배치값
    - subdivisions: 배치값을 얼마로 분할하여 학습할건지 (out of memory 발생시 값을 적절히 올릴것)
        - 예) 8, 16, 32, 64
    - width, height: 이미지 사이즈
        - 32배 단위로 사용하는 듯
        - 기본값은 416이지만, 608등 변경 가능
        - 이미지가 클수록 정확도는 올라가지만, 학습 시간이 오래걸림
    - control + f로 yolo 검색 후 값 수정(세 군대) 단, 필더 값은 직접 연산하여 입력해야 함
        - classes = 분류할 클래스 개수
        - filters = (4+1+클래스 개수)*3
    - mosaic: 기본값은 1이지만, 0으로 해야 작동됨 (이유는 아직 알지못함)
    - 기타 다른 변수는 [링크](https://eehoeskrap.tistory.com/370) 참조

### 4. yolov4.conv.137 다운로드
* [링크](https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.conv.137) 클릭하여 다운로드
* 다운로드 후 darknet 폴더로 이동

### 5. Makefile
* 사용 여부에 따라 변수 수정
* 예)
    ```python
    GPU=1
    CUDNN=1
    CUDNN_HALF=0
    OPENCV=0
    AVX=0
    OPENMP=0
    LIBSO=1
    ZED_CAMERA=0
    ZED_CAMERA_v2_8=0
    ```
* 수정 후 터미널에 make 실행
    ```python
    make
    ```

### 6. 학습 실행
```python
./darknet detector train custom/custom.data custom/yolov4.cfg yolov4.conv.137
```
* 학습된 모델은 backup에 생성됨 (final, last, 1000, 2000 등.. 이름으로 중간중간 저장됨)