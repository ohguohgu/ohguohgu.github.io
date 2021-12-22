---
layout: post
title:  "백준 알고리즘 2739번 #PYTHON"
subtitle: "백준 알고리즘 2739번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> N을 입력받은 뒤, 구구단 N단을 출력하는 프로그램 작성  
> 입력 : 첫째 줄에 N이 주어진다. N은 1보다 크거나 같고 9보다 작거나 같다.  
> 출력 : 출력형식과 같게 <N*1>부터 <N*9>까지 출력한다.  

## 02. 문제 풀이
```python
num = int(input())
for i in range(1,10): # for문을 통해 1부터 9까지 반복
    print(num, "*", i, "=", num*i)
```