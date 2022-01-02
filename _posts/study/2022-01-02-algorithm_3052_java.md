---
layout: post
title:  "백준 알고리즘 3052번 #JAVA"
subtitle: "백준 알고리즘 3052번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명
> <b>1차원배열 예제</b>    

> 두 자연수 A와 B가 있을 때, A%B는 A를 B로 나눈 나머지 이다. 예를 들어, 7, 14, 27, 38을 3으로 나눈 나머지는 1, 2, 0, 2이다.    
> 수 10개를 입력받은 뒤, 이를 42로 나눈 나머지를 구한다. 그 다음 서로 다른 값이 몇 개 있는지 출력하는 프로그램을 작성하시오.   
  
> <b>입력 : </b>첫째 줄부터 열번째 줄 까지 숫자가 한 줄에 하나씩 주어진다. 이 숫자는 1,000보다 작거나 같고, 음이 아닌 정수이다.  
  
> <b>출력 : </b>첫째 줄에, 42로 나누었을 때, 서로 다른 나머지가 몇 개 있는지 출력한다.  

## 02. 문제 풀이(1)
#### -HashSet 클래스를 이용해서 서로 다른 나머지의 갯수를 구한다.

```JAVA

import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        HashSet<Integer> result = new HashSet<Integer>();
        for(int i=0; i<10; i++){
            result.add(Integer.parseInt(bf.readLine())%42);
        }
        // HashSet.size()는 HashSet의 크기를 반환
        System.out.print(result.size());
    }
}
```

## 02. 문제 풀이(2)
#### -배열을 만들어서 배열에 나머지 저장하여 갯수를 구한다.
```JAVA
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws IOException{
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        
        // 나머지가 나올 수 있는 최대 갯수가 42기 때문에 배열의 길이를 42로 초기화시켜준다.
        boolean[] arr = new boolean[42];
        
        for(int i=0; i<10; i++) {
            // 배열 안에 값이 있는지 확인하기 위해 true를 넣어준다.
            arr[Integer.parseInt(bf.readLine() % 42)] = true;
        }
        
        int cnt = 0;
        for(boolean val:arr) {
            if(val) cnt++;
        }
        System.out.print(cnt);
    }
}
```