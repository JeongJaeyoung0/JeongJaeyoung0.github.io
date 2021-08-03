---
layout: post
title: "[Setting] 구글 코랩에서 실행하기 (하이퍼링크)"
subtitle: "googlecolabrunhyperlink"
categories: python
tags: setting
comments: true
---

# 구글 코랩에서 실행하기 (하이퍼링크) 적용 방법
### 깃허브에 업로드한 파일을 구글 코랩에서 실행하는 하이퍼링크

* * *

<table align="left">
  <td>
    <a target="_blank" href="https://colab.research.google.com/github/<<<https://github.com 제외한 깃허브 파일 주소 입력>>>"><img src="https://www.tensorflow.org/images/colab_logo_32px.png" />구글 코랩에서 실행하기</a>
  </td>
</table>

<br>
<br>
<br>

1. 하이퍼링크 적용할 곳에 아래 코드 입력
2. <<< >>> 위치에 깃허브에 업로드한 파일의 주소 중 https://github.com를 제외한 주소 입력
    * 예) 깃허브 주소 : https://github.com/JeongJaeyoung0/function/blob/main/example.ipynb
    * 입력) href="https://colab.research.google.com/github/JeongJaeyoung0/function/blob/main/example.ipynb"
<pre><code>
<table align="left">
  <td>
    <a target="_blank" href="https://colab.research.google.com/github/<span style="color: red;"><<<https://github.com 제외한 깃허브 파일 주소 입력>>></span>"><img src="https://www.tensorflow.org/images/colab_logo_32px.png" />구글 코랩에서 실행하기</a>
  </td>
</table>
</code></pre>