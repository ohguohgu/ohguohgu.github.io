---
layout: post
title:  "백준 알고리즘 10950번 #PYTHON"
subtitle: "백준 알고리즘 10950번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램 작성  
> 입력 : 첫째 줄에 테스트 케이스의 개수 T를 입력, 각 테스트 케이스는 한줄로 입력하며 공백을 통해 A와 B를 구분  
> 출력 : 각 테스트 케이스마다 A+B를 출력  

## 02. 문제 풀이
```python
t = int(input()) #반복할 횟수 입력

for i in range(t):
    A,B = map(int, input().split()) #A와 B 입력
    print(A+B) #결과값 출력
```