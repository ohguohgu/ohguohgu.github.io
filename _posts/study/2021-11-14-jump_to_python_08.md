---
layout: post
title:  "점프 투 파이썬 - 05-6장 라이브러리"
subtitle:   "파이썬"
categories: study
tags: python
comments: true
---
## 개요
> 파이썬의 라이브러리

## 파이썬의 라이브러리의 개념과 사용방법
---
### **01. 라이브러리(Library)**   
-라이브러리란, 도서관이란 의미와 비슷하게 원하는 정보를 찾아보는 곳이다.  
-파이썬 라이브러리는 파이썬 설치시 자동으로 설치된다.  

### **02. sys**   
-파이썬 인터프리터가 제공하는 변수 및 함수를 직접 컨트롤할 수 있게 해주는 모듈  

```
# argv_test.py 생성
>>> import sys
>>> print(sys.argv)

# cmd창(명령 프롬프트)에서 실행
C:/argv_test.py경로> python argv_test.py you need python
['argv_test.py','you','need','python'] --> python 명령어 뒤의 모든 단어들이 공백을 기준으로 리스트 요소로 출력

# sys.exit() --> 강제로 스크립트 종료

# sys.path --> 파이썬 모듈이 저장된 위치 출력

# sys.path.append('경로') --> 경로 이름 추가
```

### **03. pickle**
-객체의 형태를 유지하면서 파일에 저장하고 불러오는 모듈

```
# pickle의 dump 함수를 이용해서 data 객체를 복사
>>> import pickle
>>> f = open("test.txt","wb")
>>> data = {1:'python',2:'you need'}
>>> pickle.dump(data,f)
>>> f.close()

# pickle의 load 함수를 이용해서 data 객체를 불러옴
>>> import pickle
>>> f = open("test.text","rb")
>>> data = pickle.load(f)
>>> print(data)
{1:'python',2:'you need'}
```   

### **04. OS**
-환경 변수나 디렉터리, 파일 등의 OS 자원 제어 모듈  

```
# os.environ : 환경변수 확인
>>> import os
>>> os.environ
environ({'ALLUSERSPROFILE': 'C:\\ProgramData', 'APPDATA': 'C:\\Users\\aran\\AppData\\Roaming',.... 중략

# os.environ['PATH'] : PATH 환경변수 확인
>>> os.environ['PATH']
C:\Windows\system32;C:\Windows;C:\Windows\System32\ ... 중략

# os.chdir : 디렉터리 위치 변경
>>> os.chdir("C:\WINDOWS")

# os.getcwd : 현재 디렉터리 위치를 돌려준다
>>> os.getwd()
```

### **05. shutil**  
-파일 복사해주는 모듈  

```
# src.txt 파일을 dst.txt로 복사
>>> import shutil
>>> shutil.copy("src.txt","dst.txt")
```

### **06. webbrowser**
-시스템에서 사용하는 기본 웹브라우저를 자동으로 실행하는 모듈  
```
# 웹 브라우저로 구글 띄우기
>>> import webbrowser
>>> webbrowser.open("http://google.com")
```
