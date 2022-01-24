---
layout: post
title:  "백준 알고리즘 1152번 #JAVA"
subtitle: "백준 알고리즘 1152번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명

> 영어 대소문자와 공백으로 이루어진 문자열이 주어진다. 이 문자열에는 몇 개의 단어가 있을까? 이를 구하는 프로그램을 작성하시오.  
> 단, 한 단어가 여러 번 등장하면 등장한 횟수만큼 모두 세어야 한다.  
  
> <b>입력 : </b>첫 줄에 영어 대소문자와 공백으로 이루어진 문자열이 주어진다. 이 문자열의 길이는 1,000,000을 넘지 않는다. 단어는 공백 한 개로 구분되며, 공백이 연속해서 나오는 경우는 없다. 또한 문자열은 공백으로 시작하거나 끝날 수 있다.  
  
> <b>출력 : </b>첫째 줄에 단어의 개수를 출력한다.  

## 02. 문제 풀이
#### -StringTokenizer 클래스의 내장함수인 countTokens()을 이용하여 공백으로 끊은 단어의 갯수를 출력한다.

```JAVA
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        try (BufferedReader bf = new BufferedReader(new InputStreamReader(System.in))) {
            StringTokenizer st = new StringTokenizer(bf.readLine()," ");
            System.out.println(st.countTokens());           
        }
    }
}
```