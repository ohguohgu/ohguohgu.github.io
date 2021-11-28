---
layout: post
title:  "백준 알고리즘 1008번 #JAVA"
subtitle: "백준 알고리즘 1008번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> 두 정수 A와 B를 입력받은 다음, A/B를 출력하는 프로그램 작성  
> 첫째줄에 A와 B가 주어진다.  
> 첫째줄에 A/B를 출력한다. __실제 정답과 출력값의 절대오차 또는 상대오차가 10-9 이하이면 정답이다.__

## 02. 문제 풀이
```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        double a = sc.nextDouble();
        double b = sc.nextDouble();
        System.out.print(a/b);
    }
}
```


**파이썬에선 int 함수 통해서 나누면 나머지 포함하여 계산된다.**
**자바에서는 int 타입으로 변수 선언시 정수로 처리되기 때문에 나머지가 없어서 정확한 값이 나오지 않는다.**