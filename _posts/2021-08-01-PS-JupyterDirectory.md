---
layout: post
title: "[Setting] jupyter 디렉토리 변경"
subtitle: "JupyterDirectory"
categories: python
tags: setting
comments: true
---

# jupyter 디렉토리 변경

* * *

1. cmd 실행
2. configure 파일 생성하기
```python
jupyter notebook --generate-config
```
3. 생성된 파일 열기

    C:\Users\컴퓨터명\.jupyter\ `jupyter_notebook_config`

4. `#` 삭제, 노란색 글자에 디렉토리 지정

    * `# c.NotebookApp.notebook_dir = ''` 를 아래와 같이 변경
    * `c.NotebookApp.notebook_dir = 'G:\내 드라이브'`

5. Jupyter Notebook 우클릭 > 파일 위치 열기 > Jupyter (Anaconda3) 우클릭 > 속성
    * [대상]의 `"%USERPROFILE%/"` 삭제
    * [시작 위치]의 `%HOMEPATH%` 삭제
