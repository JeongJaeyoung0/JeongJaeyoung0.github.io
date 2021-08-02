---
layout: post
title: "[anaconda] 가상환경 (64bit에서 32bit)"
subtitle: "AnacondaVirtualEnvironment64bitTo32bit"
categories: python
tags: setting
comments: true
---

## ▶ 64bit가 설치된 상황에서 32bit 가상환경 설정 방법
<ol class='counter'>
  <li> cmd 실행</li>
  <li> 버전 확인</li>
  <pre><code>python --version</code></pre>
  <li> 아나콘다 32bit 설치</li>
  <pre><code>set conda_force_32bit=1</code></pre>
  <li> 버전 값 입력 (2번의 버전 값을 3.x.x에 입력)</li>
  <pre><code>conda create -n <span style="color: red;">py38_32</span> python=3.8.5 anaconda</code></pre>
</ol>
<br>
## ▶ 설정 후 주피터 실행 방법
<ol class='counter'>
  <li> cmd 실행</li><br>
  <li> 32bit 가상환경으로 도입</li>
  <pre><code>conda activate <span style="color: red;">py38_32</span></code></pre>
  <li> 주피터 실행</li>
  <pre><code>jupyter notebook</code></pre>
  <li> bit 확인 방법</li>
    <ul>
    <li> urs창 확인</li><br>
    - localhost:8888 : 32bit<br>
    - localhost:8889 : 64bit<br>
    <li> 주피터에서 확인</li><br>
    &gt;&gt;&gt; import platform<br>
    &gt;&gt;&gt; print(platform.architecture())
    </ul>
</ol>
