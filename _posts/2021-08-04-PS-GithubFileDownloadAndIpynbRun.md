---
layout: post
title: "[Setting] github 파일 다운로드 & ipynb 파일 실행"
subtitle: "GithubFileDownloadAndIpynbRun"
categories: python
tags: setting
comments: true
---

* pythong에서 github에서 파일 다운로드
* 다운받은 ipynb 파일 실행

<br>

# ● code

***

# github 파일 다운로드


```python
!pwd
```

    /content
    


```python
!git clone https://github.com/JeongJaeyoung0/function.git   # 다운 받을 깃허브 clone 링크
```

    Cloning into 'function'...
    remote: Enumerating objects: 60, done.[K
    remote: Counting objects: 100% (60/60), done.[K
    remote: Compressing objects: 100% (59/59), done.[K
    remote: Total 60 (delta 30), reused 0 (delta 0), pack-reused 0[K
    Unpacking objects: 100% (60/60), done.
    


```python
!git pull  # 저장소에서 변경 사항을 가져오기 위한
```

    fatal: not a git repository (or any of the parent directories): .git
    


```python
%cd ./function
```

    /content/function
    


```python
!ls
```

    prime_number.ipynb  README.md
    

# ipynb 파일 실행


```python
!pip install import_ipynb   # 코랩에서 ipynb 파일 실행 하기 위한
```

    Collecting import_ipynb
      Downloading import-ipynb-0.1.3.tar.gz (4.0 kB)
    Building wheels for collected packages: import-ipynb
      Building wheel for import-ipynb (setup.py) ... [?25l[?25hdone
      Created wheel for import-ipynb: filename=import_ipynb-0.1.3-py3-none-any.whl size=2975 sha256=0906c5564de38afb8b2dad498c369fff0bad5c09c5b597e467dea5d4fb7b76f4
      Stored in directory: /root/.cache/pip/wheels/b1/5e/dc/79780689896a056199b0b9f24471e3ee184fbd816df355d5f0
    Successfully built import-ipynb
    Installing collected packages: import-ipynb
    Successfully installed import-ipynb-0.1.3
    


```python
import import_ipynb     # 라이브러리 불러오기
```


```python
from prime_number import prime_number   # n까지의 소수 리스트 출력 (에라토스테네스의 체)
```

    importing Jupyter notebook from prime_number.ipynb
    


```python
prime_number(20)
```




    [2, 3, 5, 7, 11, 13, 17, 19]




```python

```
