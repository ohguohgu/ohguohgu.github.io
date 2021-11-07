---
layout: post
title:  "점프 투 파이썬 - 04장"
subtitle:   "파이썬 함수"
categories: study
tags: python
comments: true
---
## 개요
> 함수의 기본 내용과 파이썬의 함수 사용 방법에 대한 설명 

## 함수의 의미와 파이썬 함수의 간단한 사용법
---
### **01. 함수(function)**   
-어떤 입력값을 주어졌을 때 결괏값을 돌려주는 것.  
(함수가 무조건 입력값이 있어야 하는건 아니지만 보통 입력값을 받아 결과값을 뱉어준다.)   

### **02. def**
-def라는 예약어를 통해 함수 생성

```
def 함수이름 (매개변수):
    수행할 문장

example.01
- 입력값 두개를 받아서 더한 값을 리턴해주는 함수
def plus(a,b):
    return a+b

example.02
>>> a = 2
>>> b = 4
>>> c = plus(a,b)
>>> print(c)
6
```

### **03. 매개변수와 인수**
**03-1.매개변수(parameter)**   
-함수에 입력으로 전달된 값을 받는 변수       
-def plus(a,b) --> 이때 a와 b는 매개변수    

**03-2.인수(arguments)**  
-함수를 호출할 때 함수로 전달하는 입력 값   
-plus(1,3) --> 이 때 1과 3은 인수   



### **04. 입력값이 여러개인 함수 만들기**
-매개변수의 갯수가 몇개가 될지 모르는 경우, 또는 매우 많은 경우 '*'를 추가하여 만들 수 있다.  
-매개변수 명 앞에 *를 붙이면 입력값을 전부 모아서 튜플 형태로 만들어서 전달한다.    

```
def 함수명(*매개변수명):
    수행할문장

example.01
- 입력한 매개변수 모두를 더한 결과값을 리턴해주는 함수
def plus(*args):
    result = 0
    for i in args:
        result+= i
    return result
```

### **05. 매개변수에 초기값이 있는 함수 만들기**   
-매개변수 입력 자리에 초기 값을 미리 설정한 함수   
-매개변수에 들어갈 값이 항상 변하는 것이 아닐 경우 기본 값을 설정해두면 유용하다.   
-기본값이 있는 매개변수는 제일 마지막에 자리해야한다.  
(초기값을 설정해 놓은 매개변수 뒤에 초기값을 설정해 놓지 않은 매개변수는 사용할 수 없기 때문)    

```
-입력받은 이름, 나이, 성별 정보를 출력해주는 함수, 단 성별 미입력시 남자로 인식
example.01
def introduce(name , old, man=True)
    print("나의 이름은 %s입니다." % name)
    print("나의 나이는 %d살 입니다." % old)

    if man:
        print("남자입니다.")
    else:
        print("여자입니다.")

>>> introduce('김정수', 27)
나의 이름은 김정수입니다.
나의 나이는 27살 입니다.
남자입니다.

>>> introduce('최윤지', 30, False)
나의 이름은 최윤지입니다.
나의 나이는 30살 입니다.
여자입니다.
```

### **06. lambda** 
-lambda는 함수 생성 예약어로 def와 같은 역할을 한다.    
-함수를 한줄로 간결한 형태로 작성할 때 사용한다.     
-**def와 달리 lambda는 return 명령어가 없더라도 결과값을 돌려준다.**   

```
lambda 매개변수1, 매개변수2, ... : 매개변수를 사용한 로직

example.01
>>> plus = lambda a,b:a+b   --> 매개변수 a와 b의 합을 더한 값을 리턴해주는 plus 함수 생성
>>> result = plus(1,2)      --> result라는 변수에 1,2 더한 값을 저장
>>> print(result)
3
```

### **07. input()**
-사용자 입력값을 받아주는 함수    
```
example.01
>>> a = input()
my name is ohgu --> 입력값
>>> print(a)
my name is ohgu

example.02
>>> age = input("나이를 입력하세요: ")
나이를 입력하세요: 29
>>> print(age)
29
```

### **08. print()**
-입력한 인자 값을 출력해주는 함수  
-큰 따옴표로 둘러쌓인 문자열은 + 연산과 똑같이 처리한다.  
-문자열 사이의 띄어쓰기 입력은 콤마로 한다.  
-한줄로 결과값을 출력하고 싶을 땐 매개변수 end를 이용해 끝 문자를 지정한다.    

```
example.01
>>> a = 'hi'
>>> print(a)
hi

example.02
>>> print("life" "is" "too short")
lifeistoo short

>>> print("life"+"is"+"too short")
lifeistoo short

example.03
>>> print("life","is","too short")
life is too short

example.04
>>> for i in range(10):
        print(i, end=' ')
0 1 2 3 4 5 6 7 8 9 >>>

```


