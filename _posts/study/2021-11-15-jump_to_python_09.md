---
layout: post
title:  "점프 투 파이썬 - 06장 예제 함수 만들기"
subtitle:   "파이썬"
categories: study
tags: python
comments: true
---
## 개요
> 간단한 함수 만들기

## 다양한 기능을 수행하는 함수 예제 풀기
---
### **01. 3과 5의 배수 합하기**   
-1000미만의 자연수중에서 3과 5의 배수의 총합 구하기  
-중복되어 카운팅 되지 않도록 주의
```
result = 0
for n in range(1,1000):
    if(n%3 == 0 or n%5 == 0): --> or 조건으로 한번에 해결 (아니면 15같은 자연수는 3과 5 모두의 배수이기 때문에 중복 처리)
        result+=n
print(result)
```

### **02. 게시판 페이징**   
-한 페이지에서 보여줄 포스트 수와 포스트의 총 갯수 입력시 총 페이지수 구하기

```
def getPageCount(total,count):
    if(total%count == 0):
        result = total//count --> 총 포스트수와 한 페이지의 포스트 수가 딱 맞춰 떨어질 땐 나눴을 때 값 그대로 페이지 출력
    else:
        result = total//count+1 --> 아닐 경우, 나눈 값 + 1
    return result

page = getPageCount(100,27) --> 4페이지 나와야함
print(page)
```

### **03. 메모장 만들기**
-옵션과 입력값을 받아서 메모장 자동 저장 및 저장된 메모 출력하기
-'-a'입력시 메모추가, '-v'입력시 입력된 메모 출력
```
import sys
option = sys.argv[1]

if option == '-a':
    memo = sys.argv[2]
    f = open('memo.txt','a')
    f.write(memo)
    f.write('\n')
    f.close()
elif option == '-v':
    f = open('memo.txt')
    memo = f.read()
    f.close()
    print(memo)

print('END')
```   

### **04. 탭(tab)을 4개의 공백으로 바꾸기**
-문서 파일을 읽어서 그 문서 안에 있는 탭(tab)을 공백 4개로 바꿔서 새로운 파일로 저장  
```
import sys
src = sys.argv[1] --> 읽을 메모 파일
dst = sys.argv[2] --> 새로 저장할 메모 파일

f = open(src)
data = f.read()
f.close()
space_del_data = data.replace("\t"," "*4)

f = open(dst,'w')
f.write(space_del_data)
f.close()
```
### **05. 해당경로 이하에 있는 파이썬 파일 출력하기**
-C:/디렉터리 이하에 있는 파이썬 파일 출력하는 함수 만들기
```
import os

def search(dirname):
    try:
        filenames = os.listdir(dirname)
        for filename in filenames:
            full_filename = os.path.join(dirname,filename)
            if (os.path.isdir(full_filename)):
                search(full_filename) --> 재귀호출 : 자기 자신을 다시 호출하는 것
            else:
                ext = os.path.splitext(full_filename)[-1] --> os.path.splitext를 통해 확장자와 파일이름 분리
                if(ext == '.py'): --> 확장자가 .py인 파일 즉 파이썬 파일일 때 
                    print(full_filename)
    except PermissionError:
        pass

search("C:/")
```