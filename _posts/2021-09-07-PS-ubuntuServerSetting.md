---
layout: post
title: "[Setting] 우분투 서버 셋팅"
subtitle: "ubuntuServerSetting"
categories: python
tags: setting
comments: true
---

* 설치 버전
    - OS : Ubuntu 18.04 64bit
    - Nvidia 드라이버 : nvidia-driver-470
    - Cuda : 11.4
    - Cudnn : 8.2.0

* [참고](https://www.2cpu.co.kr/lec/3998) (GPU 드라이버 + CUDA + cuDNN 설치)

* * *

0. 서버에 우분투 18.04 설치 (구글링)

1. ubuntu 패키지 업데이트 및 추가 라이브러리 설치
    ```
    sudo apt update
    sudo apt install -y build-essential
    sudo apt-get install -y freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev libglfw3-dev libgles2-mesa-dev
    sudo apt-get install -y libfreeimage3 libfreeimage-dev
    ```

2. nouveau 드라이버 설치 확인
    ```
    lsmod | grep nouveau
    ```

* nouveau 드라이버 blacklist 등록
    ```
    # 파일생성
    sudo vi /etc/modprobe.d/blacklist-nouveau.conf

    # 생성된 파일에 아래 내용 작성
    blacklist nouveau
    options nouveau modeset=0
    ```

* 커널 리빌드 및 재부팅, nouveau 비활성화 확인
    ```
    sudo update-initramfs –u
    sudo reboot
    lsmod | grep nouveau
    ```

3. nvidia 그래픽 드라이버 설치 가능 버전 확인
    ```
    sudo apt install -y ubuntu-drivers-common
    ubuntu-drivers devices
    ```

* Repository 추가
    ```
    sudo add-apt-repository ppa:graphics-drivers/ppa
    입력 후 중간에 ENTER 입력 필요
    sudo apt update
    ```

* 설치가능 nvidia 드라이버 목록 확인 및 설치
    ```
    apt-cache search nvidia | grep nvidia-driver
    sudo apt install -y nvidia-driver-470
    sudo reboot
    ```

* 그래픽 드라이버 설치 확인
    ```
    nvidia-smi
    ```

4. cuda dependency 설치<br>
* [링크](https://teddylee777.github.io/linux/%EB%94%A5%EB%9F%AC%EB%8B%9D-PC%EC%97%90-ubuntu%EC%99%80-CUDA-GPU%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)
    에서 cuda를 설치하기 위한 dependency를 설치
    ```
    sudo apt-get update
    sudo apt-get install build-essential dkms
    sudo apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev
    ```

* cuda 11.4 설치 <br>
    * [참고](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=18.04&target_type=runfile_local)

    ```
    # 설치할때 드라이버설치는 반드시 체크 해제
    wget https://developer.download.nvidia.com/compute/cuda/11.4.1/local_installers/cuda_11.4.1_470.57.02_linux.run
    sudo sh cuda_11.4.1_470.57.02_linux.run

    # 경로 설정
    sudo sh -c "echo 'export PATH=$PATH:/usr/local/cuda-11.4/bin' >> /etc/profile"
    sudo sh -c "echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.4/lib64' >> /etc/profile"
    sudo sh -c "echo 'export CUDADIR=/usr/local/cuda-11.4' >> /etc/profile"
    source /etc/profile
    ```

5. cudnn 8.22 설치
* [링크](https://developer.nvidia.com/cudnn) 에서 os와 cuda 버전에 맞게 cudnn 다운로드
* cuDNN Library for Linux (x86_64) 다운로드 후 서버로 전송
    ```
    tar -zxf cudnn-11.4-linux-x64-v8.2.2.26.tgz
    sudo cp cuda/include/cudnn*.h /usr/local/cuda/include
    sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda/lib64
    sudo chmod a+r /usr/local/cuda/include/cudnn*.h /usr/local/cuda/lib64/libcudnn*
    ```
* cudnn 설치 확인
    ```
    cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
    ```

6. opencv 설치
* [참고](https://gist.github.com/raulqf/f42c718a658cddc16f9df07ecc627be7) 하여 설치

7. docker 설치
* [참고](https://docs.docker.com/engine/install/ubuntu/)
    ```
    sudo apt-get update

    sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg-agent \
        software-properties-common

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    sudo apt-key fingerprint 0EBFCD88

    sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"

    sudo apt-get update

    sudo apt-get install docker-ce docker-ce-cli containerd.io
    ```
* 위 명령을 입력하여 도커를 설치한 후 현재 사용자를 도커 그룹에 추가
    ```
    sudo usermod -aG docker 사용자계정
    ```

8. nvidia 도커 설치
* [링크](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker) 에서 nvidia 도커를 설치
    ```
    curl https://get.docker.com | sh && sudo systemctl start docker && sudo systemctl enable docker

    distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
    && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
    && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
    
    curl -s -L https://nvidia.github.io/nvidia-container-runtime/experimental/$distribution/nvidia-container-runtime.list | sudo tee /etc/apt/sources.list.d/nvidia-container-runtime.list
    sudo apt-get update

    sudo apt-get install -y nvidia-docker2

    sudo systemctl restart docker

    # nvidia 도커 설치 테스트
    sudo docker run --rm --gpus all nvidia/cuda:11.0-base nvidia-smi
    ```

* * *

99. GPU 드라이버, cuda, cudnn 삭제
* [참고](https://driz2le.tistory.com/254)

* 기본 드라이버 삭제
    ```
    # nouveau 제거 및 blacklist 등록
    # 아래 경로에 blacklist 파일을 생성
    sudo vi /etc/modprobe.d/blacklist-nouveau.conf

    # 생성된 .conf 파일에 아래 두 줄을 입력
    blacklist nouveau
    options nouveau modset=0

    # 아래 명령어를 입력 후 재부팅
    sudo update-initramfs -u
    sudo reboot
    ```

* nvidia-driver 삭제
    ```
    # x window 서버 종료 -> 콘솔로 뜬다
    sudo service gdm stop
    ```

* 드라이버 삭제
    ```
    sudo apt purge nvidia-driver-*

    # 관련 의존성 삭제
    sudo apt autoremove
    ```

* nvidia-cuda-toolkit 제거
    ```
    sudo rm /etc/apt/sources.list.d/cuda*
    sudo apt remove --autoremove nvidia-cuda-toolkit -y
    sudo apt-get --purge remove 'cuda*' -y
    sudo apt-get autoremove --purge 'cuda*' -y
    ```

* 기존에 설치되어있는 Nvidia config 파일 의존성 파일 제거
    ```
    sudo apt-get purge nvidia*
    sudo apt remove nvidia-*
    sudo apt-get autoremove
    sudo apt-get autoclean
    ```

* cuda 설치된 폴더 삭제
    ```
    sudo rm -rf /usr/local/cuda*
    ```
    
* 삭제 완료 후 재부팅 필요
    ```
    sudo reboot
    ```