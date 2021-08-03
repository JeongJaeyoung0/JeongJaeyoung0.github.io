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
    <a target="_blank" href="https://colab.research.google.com/github/JeongJaeyoung0/function/blob/e30e4e0c90d99cab874fe8a5b280762e1f6ae3f0/%EA%B5%AC%EA%B8%80%20%EC%BD%94%EB%9E%A9%EC%97%90%EC%84%9C%20%EC%8B%A4%ED%96%89%ED%95%98%EA%B8%B0%20(%ED%95%98%EC%9D%B4%ED%8D%BC%EB%A7%81%ED%81%AC).ipynb"><img src="https://www.tensorflow.org/images/colab_logo_32px.png"/>구글 코랩에서 실행하기</a>
  </td>
</table>

<br>
<br>
<br>

1. 하이퍼링크 적용할 곳에 아래 코드 입력
2. &lt;&lt;&lt; &gt;&gt;&gt; 위치에 깃허브에 업로드한 파일의 주소 중 https://github.com를 제외한 주소 입력
    * 예) 깃허브 주소 : https://github.com/a/b/test.ipynb
    * 입력) href="https://colab.research.google.com/github/a/b/test.ipynb"

```
<table align="left">
  <td>
    <a target="_blank" href="https://colab.research.google.com/github/<<<https://github.com 제외한 깃허브 파일 주소 입력>>>"><img src="https://www.tensorflow.org/images/colab_logo_32px.png"/>구글 코랩에서 실행하기</a>
  </td>
</table>
```