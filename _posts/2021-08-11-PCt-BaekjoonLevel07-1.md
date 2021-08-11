---
layout: post
title: "[Coding test] Baekjoon_level 7_문자열-1"
subtitle: "BaekjoonLevel7-1"
categories: python
tags: codingtest
comments: true
---

* 아스키 코드<br>
    · `ord()`: 문자를 아스키 코드로 변환<br>
    · `chr()`: 아스키 코드 값을 문자로 변환

```python
>>> ord('a')
    Out: 97

>>> chr(97)
    Out: 'a'
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/c982890290749c755a5a6512086ee2187125962b/210530_Baekjoon_coding%20test_level%207_%EB%AC%B8%EC%9E%90%EC%97%B4-1.ipynb)

***

2021.05.30
# coding test_Baekjoon_level 7_문자열-1


```python
# 11654 (아스키 코드)-1
a=input()
try:print(ord(a))
except:print(chr(a))
```

    z
    122
    


```python
# 11654 (아스키 코드)-2
print(ord(input()))
```

    0
    48
    


```python
# 11720 (숫자의 합)-1
input();print(sum([int(i) for i in input()]))
```

    11
    10987654321
    46
    


```python
# 11720 (숫자의 합)-2
input();print(sum(map(int,input())))
```

    5
    54321
    15
    


```python
# 10809 (알파벳 찾기)-1
# 소문자 입력, 위치 출력
t=input()
print(*[t.find(i)for i in [chr(a)for a in range(ord('a'),ord('z')+1)]])
```

    1 0 -1 -1 2 -1 -1 -1 -1 4 3 -1 -1 7 5 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1
    


```python
# 10809 (알파벳 찾기)-2
print(*map(input().find,map(chr,range(97,123))))
```

    abbcz
    0 1 3 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 4
    


```python
# 2675 (문자열 반복)-1
for i in range(int(input())):
    a=input()
    r=a[0]
    t=a[2:]
    print(''.join([int(r)*i for i in t]))
```

    2
    3 ABC
    AAABBBCCC
    5 /HTP
    /////HHHHHTTTTTPPPPP
    


```python
# 2675 (문자열 반복)-2
exec("r,_,*t=input();print(''.join(i*int(r)for i in t));"*int(input()))
```

    2
    3 ABC
    AAABBBCCC
    5 /HTP
    /////HHHHHTTTTTPPPPP
    


```python
# 1157 (단어 공부)-1
a=input().upper()
b="".join(set(a))
c=[[a.count(i),i] for i in b]
c.sort(reverse=True)
d=a if len(a)==1else'?'if c[0][0]==c[1][0]else c[0][1]
print(d)
```

    baaa
    A
    


```python
# 1157 (단어 공부)-2
s=input().upper();c=s.count;*_,a,b=v=sorted({*s,'?'},key=c);print(v[-(c(a)<c(b))])
```

    abcccddzz
    C
    
