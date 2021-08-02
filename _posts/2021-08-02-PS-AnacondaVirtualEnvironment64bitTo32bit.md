---
layout: post
title: "[anaconda] 가상환경 (64bit에서 32bit)"
subtitle: "AnacondaVirtualEnvironment64bitTo32bit"
categories: python
tags: setting
comments: true
---

# 64bit가 설치된 상황에서 32bit 가상환경 설정 방법

* * *

## ● 가상환경 설정
1. cmd 실행
2. 버전 확인
```python
python --version
```
3. 아나콘다 32bit 설치
```python
set conda_force_32bit=1
```
4. 버전 값 입력 (2번의 버전 값을 3.x.x에 입력)
    <pre><code>conda create -n <span style="color: red;">py38_32</span> python=3.8.5 anaconda</code></pre>
<br>

## ● 설정 후 주피터 실행 방법

1. cmd 실행
2. 32bit 가상환경으로 도입
    <pre><code>conda activate <span style="color: red;">py38_32</span></code></pre>

3. 주피터 실행
    ```python
    jupyter notebook
    ```
4. bit 확인 방법

    * urs창 확인
      - localhost:8888 : 32bit
      - localhost:8889 : 64bit
    * 주피터에서 확인<br>
        &gt;&gt;&gt; import platform<br>
        &gt;&gt;&gt; print(platform.architecture())
