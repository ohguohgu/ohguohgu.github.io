---
layout: post
title:  "백준 알고리즘 1000번 #JAVA"
subtitle: "백준 알고리즘 1000번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램 작성  
> 첫째줄에 A와 B가 주어진다.  
> 첫째줄에 A+B를 출력한다.

## 02. 문제 풀이
```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        System.out.print(a+b);
    }
}
```