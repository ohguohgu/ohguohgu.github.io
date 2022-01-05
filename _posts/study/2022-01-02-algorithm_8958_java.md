---
layout: post
title:  "백준 알고리즘 8958번 #JAVA"
subtitle: "백준 알고리즘 8958번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> <b>1차원배열 예제</b>    

> "OOXXOXXOOO"와 같은 OX퀴즈의 결과가 있다. O는 문제를 맞은 것이고, X는 문제를 틀린 것이다.  
> 문제를 맞은 경우 그 문제의 점수는 그 문제까지 연속된 O의 개수가 된다. 예를 들어, 10번 문제의 점수는 3이 된다.  
> "OOXXOXXOOO"의 점수는 1+2+0+0+1+0+0+1+2+3 = 10점이다.   
> OX퀴즈의 결과가 주어졌을 때, 점수를 구하는 프로그램을 작성하시오.  
  
> <b>입력 : </b>첫째 줄에 테스트 케이스의 개수가 주어진다. 각 테스트 케이스는 한 줄로 이루어져 있고, 길이가 0보다 크고 80보다 작은 문자열이 주어진다. 문자열은 O와 X만으로 이루어져 있다.  
  
> <b>출력 : </b>각 테스트 케이스마다 점수를 출력한다.  

## 02. 문제 풀이
#### -배열에 OX퀴즈 결과값을 저장하여 for문을 돌며 점수 계산한다.

```JAVA

import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        String[] arr = new String[Integer.parseInt(bf.readLine())];
        
        // 1.배열에 입력값을 저장한다.
        for(int i=0;i<arr.length;i++) {
            arr[i]=bf.readLine();
        }

        // 2.입력한 OX퀴즈 배열을 돌면서 계산 시작
        for(String str:arr) {
            int score=0;
            int sum=0;

            // 문자열(OX퀴즈)을 charAt()함수를 통해 하나씩 끊어서 점수 계산
            for(int j=0; j<str.length(); j++) {
                if((str.charAt(j)) == 'O') score++;
                else score=0;
                sum+=score;
            }
            System.out.println(sum);
        }
    }
}
```