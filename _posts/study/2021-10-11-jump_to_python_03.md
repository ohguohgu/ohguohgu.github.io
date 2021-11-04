---
layout: post
title:  "점프 투 파이썬 - 03장"
subtitle:   "파이썬 제어문"
categories: study
tags: python
comments: true
---
## 개요
> 파이썬의 여러가지 제어문 설명

## 파이썬 제어문과 간단한 사용법
---
### **01-1. if문**   
조건에 따라 프로그램을 실행하도록 하는 제어문   
같은 if문을 타는 수행문들은 들여쓰기를 맞춰야 함.   
들여쓰기는 탭 또는 스페이스바 4개를 사용.   
```
>>> money = True
>>> if money:
        print("택시타기")
    else:
        print("걸어가기")

택시타기 ---> 결과
```

### **01-2. elif문**
if문 이하에 여러개의 조건을 구분할 때 사용하는 제어문   
```
>>> money = True
>>> pocket = ['cellphone', 'postit']
>>> if 'card' in pocket:
        print("택시타기")
    elif money:
        print("버스타기")
    else:
        print("걸어가기")

버스타기 ---> 결과
```

### **01-3. 조건부 표현식**
파이썬에서 지원하는 축약 표현식   
```
조건문이 참인 경우 수행 if 조건문 else 조건문이 거짓인 경우
```

### **02. while문**
while : ~ 동안 이라는 사전적 의미처럼 조건에 맞는 동안 프로그램을 반복 실행하는 제어문
```
* 10번찍어 안넘어가는 나무 없다 라는 속담 표현 예제
>>> hit = 0
>>> while hit < 10:
        hit+=1
        print("나무를 %d번 찍었습니다." % hit)
        if hit == 10:
            print("나무가 넘어갑니다.")

* 1부터 10까지의 숫자중에 짝수만 더해서 출력하는 예제
>>> result = 0
>>> num = 0
>>> while num < 10:
        num+=1
        if num%2 == 0 :
            result+=num
>>> print(result)
30 ---> 결과
```

### **03. for문**   
리스트, 튜플, 문자열의 첫 번째 요소부터 마지막 요소까지 차례로 변수에 대입하여 반복 실행하는 제어문   
```
>>> list = ['one','two','three']
>>> for a in list:
        print(a)

one
two
three

* 시험점수가 60점이 넘으면 합격 출력, 넘지 않으면 불합격 출력하는 예제
>>> score = [90, 25, 67, 45, 80]
>>> num = 0
>>> for a in score:
        num+=1
        if a > 60:
            print("%d번 학생 합격" % num)
        else :
            print("%d번 학생 불합격" % num)
```