---
layout: post
title:  "백준 알고리즘 2884번 #PYTHON"
subtitle: "백준 알고리즘 2884번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> 알람 45분 일찍 설정하기 
> 입력 : 첫째줄에 시와 분을 입력한다.  
> 출력 : 입력값에서 45분이 빠른 시간이 출력된다. 

## 02. 문제 풀이
```python
h,t = int(input().split())
t-=45 # 입력한 분에서 45분을 뺀다

# 입력시간 - 45분 했을 때 0 보다 작으면 시와 분을 세팅해준다
if(t < 0):
    # 0시일땐 23시 출력
    if(h == 0):
        h = 23
    # 그외 시간은 입력값에서 1을 빼준다
    else:
        h -= 1
    t = 60+t

print(h, t)
```