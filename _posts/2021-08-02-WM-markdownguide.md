---
layout: post
title: "[MD] markdown guide"
subtitle: "markdownguide"
categories: webapp
tags: markdown
comments: true
---

# [MD] markdown guide

* * *

## 1. Headers
```
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6
```
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6

<br>

## 2. BlockQuote
```
> First blockqute.<br>
>	> Second blockqute.
```
> First blockqute.<br>
>	> Second blockqute.

<br>

## 3. list
### ● 순서 O
```
1. 첫 번째
2. 두 번째
3. 세 번째
```
1. 첫 번째
2. 두 번째
3. 세 번째
### ● 순서 X ( `*` , `+` , `-` )
    * A
      + B
        - C
          * D
    
* A
  + B
    - C
      * D

<br>

## 4. Code
### 4.1. 들여쓰기 (한줄 띄워쓰지 않으면 안됨)
```
가나다

    ABC
    
123
```
*****
가나다

    ABC
    
123
*****

<br>

### 4.1. Code block
* `<pre><code>{Code}</code></pre>` 이용 방법

```
<pre>
<code>
test code
</code>
</pre>
```
<pre><code>test code</code></pre>

* (```) 이용 방법

<pre><code>```
test code
```</code></pre>

```
test code
```

* 문법강조(Syntax highlighting)

<pre><code>```python
import numpy as np
for i in range(10):
    print('Hello world', i)
```</code></pre>

```python
import numpy as np
for i in range(10):
    print('Hello world', i)
```

<br>

## 5. Horizontal line

```
* * *
***
*****
- - -
---------------------------------------
```

* * *
***
*****
- - -
---------------------------------------

<br>

## 6. Link
```
Link test: [Google](https://google.com, "google link")

Link test: <https://google.com>
```
Link test: [Google](https://google.com, "google link")

Link test: <https://google.com>

<br> 

## 7. Bold
```
ABC**DEF**HIG
ABC~~DEF~~HIG
```
ABC**DEF**HIG

ABC~~DEF~~HIG

<br>

## 8. Image
```
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")
```
![Image test](https://www.lotus-qa.com/wp-content/uploads/2020/02/testing.jpg)
![Image test](https://www.lotus-qa.com/wp-content/uploads/2020/02/testing.jpg "Image test")

사이즈 조절 기능은 없기 때문에 ```<img width="" height=""></img>```를 이용한다.

예
```
<img src="/path/to/img.jpg" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<img src="/path/to/img.jpg" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img>
```

<img src="https://www.lotus-qa.com/wp-content/uploads/2020/02/testing.jpg" width="300px" height="170px" title="px(픽셀) 크기 설정" alt="Image test"></img><br/>
<img src="https://www.lotus-qa.com/wp-content/uploads/2020/02/testing.jpg" width="40%" height="40%" title="%(비율) 크기 설정" alt="Image test"></img>

<br>

## 9. Line break
```
마지막 3칸 이상을 띄우면 줄 바꿈이 된다.   
줄 바꿈
```
마지막 3칸 이상을 띄우면 줄 바꿈이 된다.   
줄 바꿈