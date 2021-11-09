---
layout: post
title:  "점프 투 파이썬 - 05-2장 모듈"
subtitle:   "파이썬"
categories: study
tags: python
comments: true
---
## 개요
> 파이썬의 모듈의 간략한 설명과 사용법

## 파이썬의 모듈(Module)
---
### **01. 모듈**   
-모듈이란 함수, 또는 변수, 클래스를 모아 놓은 파일이다.  
-모듈은 다른 파이썬 프로그램을 불러와 사용할 수 있게끔 만든 파이썬 파일이라고도 할 수 있다.
  
```
# mod1.py
>>> def add(a,b):
        return a+b

>>> def sub(a,b):
        return a-b

# cmd창에서 모듈 불러오기
cd /모듈 저장한 경로      --> 모듈 저장한 경로로 이동
python                   --> 대화형 인터프리터 실행
>>> import mod1          --> mod1 불러오기 (.py 확장자 입력하지 않는다.)
>>> print(mod1.add(1,2)) --> 모듈 안에 있는 함수 호출
3

# cmd창에서 모듈이름없이 함수불러오기 (모든 함수를 불러올 땐 * 사용)
>>> from mod1 import add
>>> add(3,4)
7

>>> from mod1 import add,sub
>>> add(3,4)
7
>>> sub(10,2)
8
```

### **02. __name__ 과 __main__**
-[__name__]변수는 파이썬 내부적으로 사용하는 변수명으로 cmd창에서 직접 모듈 파일을 실행할 경우 __name__ 변수에 __main__ 값이 들어간다.  
-파이썬 쉘이나 파이썬 모듈에서 실행할 경우 __name__ 변수에는 모듈 이름값이 들어간다.