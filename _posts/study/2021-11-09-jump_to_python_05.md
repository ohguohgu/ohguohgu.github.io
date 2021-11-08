---
layout: post
title:  "점프 투 파이썬 - 05-1장 클래스"
subtitle:   "파이썬"
categories: study
tags: python
comments: true
---
## 개요
> 파이썬의 클래스

## 클래스의 의미와 클래스의 간단한 활용법
---
### **01. 클래스(Class)**   
-클래스란, 무엇인가를 계속해서 찍어낼 수 있는 설계도면  
-클래스 안에서 선언한 함수는 메서드(method)라고 부른다.  
```
example.01  
사칙연산 클래스 만들기  

>>> class FourCal:
        def setData(self, first, second):
            self.first = first
            self.second = second
    --self 매개변수는 객체를 호출할 때 호출한 객체 자신이 전달되기 때문에 따로 인자를 입력할 필요가 없다.

        def add(self):
            result = self.first+self.second
            return result

        def mul(self):
            result = self.first*self.second
            return result

        def sub(self):
            result = self.first-self.second         
            return result
        
        def div(self):
            result = self.first/self.second
            return result
```

### **02. 객체(Object)와 인스턴스(instance)**
-객체와 인스턴스란, 클래스를 통해 생성된 것   
```
객체와 인스턴스의 차이점
>>> class Cookie:
        pass

>>> a = Cookie()
이 때 a는 객체이다.  
그리고 a는 Cookie의 인스턴스이다.  
즉 인스턴스라는 단어는 특정한 객체가 어떤 클래스의 객체인지 관계를 설명할 때 사용한다.
```

### **03. 생성자(Constructor)**
-생성자(Constructor)란 객체가 생성될 때 자동으로 호출되는 메서드  
-클래스 사용시 초기값을 설정해야 할 필요가 있을 때 (setData와 같은 메서드 기능) 사용  
-파이썬 메서드 이름으로 __init__을 사용하면 이메서드는 생성자로 인식한다.  
(init 앞,뒤에는 언더바 두개를 붙여 쓴 것)  

```
example.02  
사칙연산 클래스에 생성자 추가하기  
-example.01 클래스는 생성자가 없기 때문에 setData 메서드를 통해 초기값을 세팅해야만 정상적으로 작동한다.  
-example.02 클래스는 생성자가 있기 때문에 setDate 메서드를 사용하지 않고 기본값 세팅이 되지만 초기 FourCal 객체를 생성할 때, 생성자가 바로 호출되기 때문에 인자값을 넘겨줘야한다.
>>> class FourCal:
        def __init__(self, first, second):
            self.first = first
            self.second = second

        def setData(self, first, second):
            self.first = first
            self.second = second

        def add(self):
            result = self.first+self.second
            return result

        def mul(self):
            result = self.first*self.second
            return result

        def sub(self):
            result = self.first-self.second         
            return result
        
        def div(self):
            result = self.first/self.second
            return result

>>> a = FourCal() --> TypeError:__init__() missing 2 required positional arguments  
>>> a = FourCal(1,2) --> first = 1, second = 2로 세팅
```
### **04. 상속(Inheritance)**
-상속이란 말 그대로 '물려받다'라는 의미로 사용  
-a 클래스를 만들 때 b 클래스의 기능을 물려받는 것  
```
class 클래스명(상속할 클래스명)
```
-클래스를 상속하기 위해서는 클래스 이름 뒤 괄호 안에 상속할 클래스 이름 작성  
```
example.03
>>> class MoreFourCal(FourCal):
        pass

>>> a = MoreFourCal(4,2) --> MoreFourCal에 관한 인스턴스 생성
>>> a.add()              --> MoreFourCal 클래스 안에 add 메서드가 없지만 FourCal 클래스를 상속받았기 때문에 사용할 수 있다.
6
```

### **05. 오버라이딩(Overriding)**
-오버라이딩(덮어쓰기)란 상속받은 클래스에 있는 메서드를 동일한 이름으로 다시 작성하는 것  
-오버라이딩하면 부모(상속한 클래스)의 메서드가 아닌 재정의한 메서드가 호출된다.  

### **06. 클래스변수**
-클래스 내부에서 선언한 변수  
-각 각의 객체라도 같은 클래스를 통해 만들었다면 같은 클래스 변수를 사용할 수 있다.
```
>>> class Info:
        addr = "bucheon"

>>> print(Info.addr)
bucheon

-- a와 b라는 객체 생성
>>> a = Info()
>>> b = Info()

-- 각 각의 객체지만 같은 addr 변수 값을 사용 (동일한 값)
>>> print(a.addr)
bucheon
>>> print(b.addr)
bucheon

-- 클래스 변수 값 변경
>>> Info.addr = "seoul"

-- a, b 객체 모두 값이 변경
>>> print(a.addr)
seoul
>>> print(b.addr)
seoul
```
