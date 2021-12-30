---
layout: post
title:  "백준 알고리즘 2577번 #JAVA"
subtitle: "백준 알고리즘 2577번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> <b>1차원배열 예제</b>  
> 세 개의 자연수 A, B, C가 주어질 때 A × B × C를 계산한 결과에 0부터 9까지 각각의 숫자가 몇 번씩 쓰였는지를 구하는 프로그램을 작성하시오.  
> 예를 들어 A = 150, B = 266, C = 427 이라면 A × B × C = 150 × 266 × 427 = 17037300 이 되고, 계산한 결과 17037300 에는 0이 3번, 1이 1번, 3이 2번, 7이 2번 쓰였다.  
  
> <b>입력 : </b>첫째 줄에 A, 둘째 줄에 B, 셋째 줄에 C가 주어진다. A, B, C는 모두 100보다 크거나 같고, 1,000보다 작은 자연수이다.  
  
> <b>출력 : </b>첫째 줄에는 A × B × C의 결과에 0 이 몇 번 쓰였는지 출력한다. 마찬가지로 둘째 줄부터 열 번째 줄까지 A × B × C의 결과에 1부터 9까지의 숫자가 각각 몇 번 쓰였는지 차례로 한 줄에 하나씩 출력한다.   

## 02. 문제 풀이(1)
#### -이중 for문을 이용해서 순차적으로 count 체크후 바로 출력

```JAVA

import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        
        int a = Integer.parseInt(bf.readLine());
        int b = Integer.parseInt(bf.readLine());
        int c = Integer.parseInt(bf.readLine());
        int mul = a*b*c;
        String mulStr = Integer.toString(mul);
        
        for(int i=0; i<10; i++)
        {
            int cnt = 0;
            for(int j=0; j<mulStr.length(); j++){
                if( (mulStr.charAt(j) - '0') == i)
                {
                   cnt++;
                }
            }
            System.out.println(cnt);
        }    
    }
}
```
## 02. 문제 풀이(2)
#### -배열을 만들어서 배열안에 카운트를 저장해서 출력
```JAVA
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        
        int mul = Integer.parseInt(bf.readLine())*Integer.parseInt(bf.readLine())*Integer.parseInt(bf.readLine());
        String mulStr = String.valueOf(mul);
        int[] arr = new int[10];
        
        for(int i=0; i<mulStr.length(); i++)
        {
            arr[mulStr.charAt(i)-48]++;
        }
        
        for(int result:arr){
            System.out.println(result);
        }
    }
}
```