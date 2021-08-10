---
layout: post
title: "[Coding test] Baekjoon_level 4_while문"
subtitle: "BaekjoonLevel4"
categories: python
tags: codingtest
comments: true
---

* `:=` (바다코끼리 연산자) : 표현식 결과를 키에 저장

```python
>>> a=5; b=0
>>> while(a:= a-1) : b+=1
>>> print(b)

    Out: 4
```

<br>


# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/74311c80bbdf85e17b2158b905734c7dbcd33d2e/210527_Baekjoon_coding%20test_level%204_while%EB%AC%B8.ipynb)

***

2021.05.27
# coding test_Baekjoon_level 4_while문


```python
# 10952 (A+B -5)
a=input()
while'0 0'!=a:print(eval('+'.join(a)));a=input()
```

    1 1
    2
    2 3
    5
    3 4
    7
    0 0
    


```python
# 10951 (A+B -4)
for a,_,b,_ in open(0):print(int(a)+int(b))
```


```python
# 1110 (더하기 사이클)-1
# 주어진 두자리 수를 각각 더하고 > 더한 값의 끝과 주어진 수의 1의자리 수를 더하고 > 반복하였을 때 처음 주어진 수가 나올때 까지의 사이클 수
def s(a):x=a//10;y=a%10;c=x+y;z=c%10;return int(str(y)+str(z))
n=int(input())
i=1
a=s(n)
while a!=n:a=s(a);i+=1
print(i)
```

    26
    4
    


```python
# 1110 (더하기 사이클)-2
a=n=int(input());c=1
while(a:=a%10*10+a*11//10%10)-n:c+=1
print(c)
```

    0
    1
    


```python
a=5; b=0

while( a:= a-1 ) : b+=1

print(b)
```

    4
    
