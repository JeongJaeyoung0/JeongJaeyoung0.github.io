---
layout: post
title: "[Coding test] Baekjoon_level 7_문자열-2"
subtitle: "BaekjoonLevel7-2"
categories: python
tags: codingtest
comments: true
---

* 정렬<br>
    · `[ ].sort()` : 본문을 정렬해서 변환<br>
    · `sorted([ ])` : 새로운 리스트를 반환

```python
>>> a='132423'
>>> b=sorted(a)                 # 오름차순
    Out: ['1', '2', '2', '3', '3', '4'] 

>>> b=sorted(a, reverse=True)   # 내림차순
    Out: ['4', '3', '3', '2', '2', '1']

>>> b=sorted(a,key=a.find)      # 본문 순서 그대로 정렬
    Out: ['1', '3', '3', '2', '2', '4']
```

<br>

# ● [code](https://github.com/JeongJaeyoung0/coding_test/blob/1747e842f48a1be58e1f27adb6b4b72d2342f789/210531_Baekjoon_coding%20test_level%207_%EB%AC%B8%EC%9E%90%EC%97%B4-2.ipynb)

***

2021.05.31
# coding test_Baekjoon_level 7_문자열-2


```python
# 1152 (단어의 개수)
print(len(input().split()))
```

     Mazatneunde Wae Teullyeoyo
    3
    


```python
# 2908 (상수)-1
b,a=input()[::-1].split();print(a if a>b else b)
```

    734 893
    437
    


```python
# 2908 (상수)-2
print(max(input()[::-1].split()))
```

    123 456
    654
    


```python
# 5622 (다이얼)-1
a=input()
b=['ABC','DEF','GHI','JKL','MNO','PQRS','TUV','WXYZ']
print(sum([l+3 for i in a for l in range(len(b)) if i in b[l]]))
```

    UNUCIC
    36
    


```python
# 5622 (다이얼)-2
print(sum(5*min(ord(x),88)//16-17for x in input()))
```


```python
# 2941 (크로아티아 알파벳)
a=input()
for i in ['c=','c-','dz=','d-','lj','nj','s=','z=']:a=a.replace(i,'_')
print(len(a))
```

    ljes=njak
    6
    


```python
#1316 (그룹 단어 체커)-1
import re
c=0
exec("""
b=input()
c=c+eval('*'.join(map(str,[int(len(re.sub(r'[^%s]'%(b[i]),' ',b).split()))<2 for i in range(len(b))])));"""*int(input()))
print(c)
```

    3
    happy
    abbbbbbcccc
    abcbacbc
    2
    


```python
#1316 (그룹 단어 체커)-2
a=0;exec('b=input();a+=[*b]==sorted(b,key=b.find);'*int(input()));print(a)
```

    2
    abcbbb
    aaaabbbzz
    1
    
