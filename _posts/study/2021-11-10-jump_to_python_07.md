---
layout: post
title:  "점프 투 파이썬 - 05-4장 예외처리"
subtitle:   "파이썬"
categories: study
tags: python
comments: true
---
## 개요
> 파이썬의 예외처리

## 파이썬의 예외처리 기법
---
### **01. 예외처리(Exception)**   
-파이썬은 오류가 발생하면 프로그램을 중단하고 오류 메세지를 보여준다. 이 때 오류를 사용자가 원하는 방법으로 처리해주는 것을 예외처리라 한다.
  
```
# try, except문
try:
    수행 블록
except [발생오류 [as 오류 메세지변수]]:
    오류 발생시 수행할 블록

# example.01 : 0으로 숫자를 나눌 때 나는 발생하는 에러 출력
try:
    4/0
except ZeroDivisionError as e:
    print(e)
------------------
division by zero

# example.02 : 존재하지 않는 인덱스를 호출시 인덱싱 에러 출력
try:
    a = [1,2]
    print(a[3])
except IndexError:
    print("인덱싱할 수 없습니다.")
------------------
인덱싱할 수 없습니다.
```

### **02. 오류 회피하기**
-프로그램은 때때로 에러가 발생하더라도 그냥 통과해야할 때가 있는데 그럴 때 사용하는 예외처리 방법  
```
try:
    f = open("없는파일",'r')
except FileNotFoundError:
    pass
```   

### **03. 예외 만들기**
-특수한 경우에 예외처리를 하기 위해 직접 예외를 만들어서 사용할 수 있다.  
-예외를 만들 땐 파이썬 내장 클래스인 Exception 클래스를 상속하여 만들 수 있다.  

```
# 에러 생성
class MyError(Exception):
    pass


# 함수 생성
def say_nick(nick):
    if nick=='바보':
        raise MyError(nick) --> raise 명령어를 통해 MyError 발생
    print(nick)

# 함수 호출
say_nick("천사")
say_nick("바보")

-----------------
천사
MyError 발생

# 함수 호출 예외처리
try:
    say_nick("천사")
    say_nick("바보")
except MyError:
    print("허용되지 않는 별명")

-----------------
천사
허용되지 않는 별명

# 에러 클래스에 메세지 추가
class MyError(Exception,nick):
    def __str__(self,nick):
        return "허용되지 않는 별명입니다."
```