---
layout: post
title:  "점프 투 파이썬 - 06장 정규표현식"
subtitle:   "파이썬"
categories: study
tags: python
comments: true
---
## 개요
> 파이썬의 기본 정규표현식 설명 

## 정규표현식(Regular Expressions)의 의미와 이해
---
### **01. 정규표현식이란**   
-정규표현식(Regular Expressions)란 복잡한 문자열 처리시 사용하는 기법  
-특정한 조건의 문자를 검색 또는 치환하는 과정을 간편하게 처리할 수 있는 수단  

### **02.메타문자 (meta characters)**   
-정규표현식에서 사용하는 문자  
-메타문자는 원래 그 문자의 의미와는 달리 정규표현식의 특별한 용도로 사용  

```
# 01.메타문자 종류
. ^ $ * + ? { } [ ] \ | ( )
```

### **02-1. [ ] (문자클래스)**
1)[ ] 사이의 문자들과 매치  
-[abc]의 경우 'a,b,c중 한 개의 문자와 매치'를 의미 

2)[ ] 사이에 하이픈(-) 사용시 두 문자의 범위를 의미  
-[a-c] 는 [abc]를, [0-5]는 [012345]를 의미  
-[a-zA-Z] : 알파벳 전부매치 , [0-9] : 숫자 전부 매치)  

3)[ ] 사이에 ^ 사용시 not을 의미  
-[^0-9] : 숫자가 아닌 문자만을 의미  

```
# 자주표현하는 문자 클래스 정규표현식
1) \d   
-[0-9]와 같이 숫자와 매치  

2) \D  
-[^0-9]와 같이 숫자가 아닌것과 매치  

3) \s  
-[\t\n\r\f\v]처럼 whitespace문자 (공백표현문자)와 매치  

4) \S  
-whitespace가 아닌 것과 매치   

5) \w  
-[a-zA-Z0-9_]와 매치 (문자+숫자)  

6) \W  
-문자와 숫자가 아닌것만 매치  
```   

### **02-2. . (Dot 메타문자)**  
-줄바꿈문자 (\n)을 제외한 모든 문자와 매치
```
1)a.b
-a와b사이에 \n 제외한 어떤 문자열이 오더라도 매치
-acb(yes), abc(no) 

2)a[.]b
-a와 b사이에 '.' 문자가 있으면 매치
```
### **02-3. * (반복) **
-'*' 문자 앞에 쓰인 문자가 0부터 약 2억번 정도 반복되었을 때 매치
```
1)ca*t
-a가 0부터 2억번 정도 반복되었을 때 매치
-ct (yes), cat (yes)
-ct 가 매치되는 이유는 a가 0번 반복되었다고 판단하기 때문
```

### **02-4. + (반복) **
-'+' 문자 앞에 쓰인 문자가 1부터 약 2억번 정도 반복되었을 때 매치
```
1)ca*t
-a가 1부터 2억번 정도 반복되었을 때 매치
- cat (yes), ct (no)
-'*'와 다르게 ct가 매치되지 않음
```

### **02-5. {m,n} (반복) **
-'*','+'와 다르게 반복의 횟수를 지정하여 매치  
```
1) {m}
-ca{2}t : a가 2번 반복일 때 매치
-caat (yes), cat (no)

2) {m,n}
-ca{2,5}t : a가 2번에서 5번 반복되면 매치
-cat (no), caat (yes), caaaaat (yes)
```

### **02-6. ? **
-{0,1}처럼 ? 앞에 문자가 0번 또는 1번 사용되었을 때 매치
```
1) at?c
-t가 0~1번 사용되면 매치
-ac (yes), atc (yes)
```

### **03. 파이썬 정규식 사용방법**
-파이썬은 정규식을 사용하기 위해 regular expression 모듈을 이용  
-따로 설치할 필요 없음 (파이썬 설치시 자동 설치)
```
>>> import re
>>> p = re.compile('[a-z]+') --> 컴파일된 패턴 객체

1) match()
>>> m = p.match('python')
>>> print(m)
<re.Match object; span=(0, 6), match='python'>

>>> m = p.match('3 python')
>>> print(m)
None

2) search()
>>> m = p.search("python")
>>> print(m)
<re.Match object; span=(0, 6), match='python'>

>>> m = p.search("3 python")
>>> print(m)
<re.Match object; span=(2, 8), match='python'>
--> match는 첫문자열부터 매치 확인, search는 문자열 전체를 바라보고 매치 체크

3) findall
>>> result = p.findall("life is too Short")
>>> print(result)
['life', '', 'is', '', 'too', '', '', 'hort', ''] --> 리스트로 돌려줌

>>> result = p.finditer("Life is too Short")
>>> print(result)
<callable_iterator object at 0x0000020D13C984F0> --> 반복 가능한 객체로 돌려줌 (for문을 통해 출려하면 findall의 리스트와 동일)
```

### **04. match 객체의 메서드**

|--|----------|
|group()|매치된 문자열|
|start()|매치된 문자열의 시작 위치|
|end()|매치된 문자열의 끝 위치|
|span()|매치된 문자열의 시작과 끝 위치 (튜플형태)|


```
>>> import re
>>> p = re.compile('[a-z]+')
>>> m = p.match("python")
>>> m.group()
'python'
>>> m.start() --> match 함수로 매치될경우 시작점은 무조건 0
0
>>> m.end()
6
>>> m.span()
0,6
```

### **05. 컴파일(compile) 옵션**

|옵션|약어|설명|
|--|--|---|
|DOTALL|S|dot 문자가 줄바꿈 문자 포함하여 모든 문자와 매치|
|IGNORECASE|I|대,소문자 상관없이 매치|
|MULTILINE|M|여러줄과 매치|
|VERBOSE|X|주석등을 편히 사용할 수 있는 verbose 모드사용|

```
1) DOTALL
import re
p = re.compile('a.b')
m = p.match('a\nb')
print(m)
None

p = re.compile('a.b',re.DOTALL)
m = p.match('a\nb')
print(m)
<re.Match object; span=(0, 3), match='a\nb'>  --> 줄바꿈 문자도 포함하여 매치

2) IGNORECASE
import re
p = re.compile('[a-z]',re.I)
m = p.match('Python')
print(m)
<re.Match object; span=(0, 1), match='P'> --> 대,소문자 구별 없이 매치

3) MULTILINE
import re
p = re.compile("^python\s\w+")
data = """python one
life is too short
python hi
you need python"""
print(p.findall(data))
['python one'] --> 첫번째 줄만 매칭

p = re.compile("^python\s\w+", re.MULTILINE)
data = """python one
life is too short
python hi
you need python"""
print(p.findall(data))
['python one', 'python hi'] --> 각줄마다 매칭

4) VERBOSE
-복잡한 정규식 표현 할 때 사용하는 옵션으로 화이트스페이스를 비롯해서 # 을 통해 주석을 사용할 수 있어서 가독성을 높일 수 있다. 
```

### **06. 백슬래쉬 표현**
-정규표현식에서 백슬래쉬 매치를 하기 위해선 \\ 두번 작성  
-백슬래쉬를 2번 이상 매치하기 위해야할 땐 'r' 사용  
(p = re.compile(r'\\section')) --> \\section 매치