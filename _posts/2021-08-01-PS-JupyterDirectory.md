---
layout: post
title: "[Setting] jupyter 디렉토리 변경"
subtitle: "JupyterDirectory"
categories: python
tags: setting
comments: true
---

## ▶ jupyter 디렉토리 변경
<ol class='counter'>
  <li> cmd 실행</li>
  <li> configure 파일 생성하기</li>
  <pre><code>jupyter notebook --generate-config</code></pre>

  <li> 생성된 파일 열기</li><br>
  C:\Users\컴퓨터명\.jupyter\ <span style="color: red;">jupyter_notebook_config</span>

  <li> # 삭제, 노란색 글자에 디렉토리 지정</li><br>
  # c.NotebookApp.notebook_dir = '' 를 아래와 같이 변경<br>
  <span style="color: red;">c.NotebookApp.notebook_dir = '</span><span style="color: yellow;">G:\내 드라이브</span><span style="color: red;">'</span>

  <li> Jupyter Notebook 우클릭 > 파일 위치 열기 > Jupyter (Anaconda3) 우클릭 > 속성</li><br>
  [대상]의 <span style="color: red;">"%USERPROFILE%/"</span> 삭제<br>
  [시작 위치]의 <span style="color: red;">%HOMEPATH%</span> 삭제
</ol>
