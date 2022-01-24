---
layout: post
title:  "프로그래머스 정수 내림차순으로 배치하기 #JAVA"
subtitle: "정수 내림차순으로 배치하기"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명

> 함수 solution은 정수 n을 매개변수로 입력받습니다.  
> n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요.  
> 예를들어 n이 118372면 873211을 리턴하면 됩니다.  

## 02. 문제 풀이
##### int 타입 배열(arr)을 생성하여 첫번째 for문을 통해 매개변수로 받아온 n을 한글자씩 저장한다.
##### 이후 이중 for문의 버블정렬 통해 내림차순으로 배열을 정리한다.
##### str 변수에 내림차순한 배열의 글자를 이어붙여준 다음 Long 타입으로 변환하여 return 한다.

```JAVA
import java.util.Arrays;
import java.util.Collections;

class Solution {
    public long solution(long n) {
        String num = String.valueOf(n);
        int [] arr = new int[num.length()];
        String str = "";
        
        for(int i=0; i<num.length(); i++) {
            arr[i] = num.charAt(i) -'0';
        }
        
        for(int i=0; i<num.length()-1; i++) {
            for(int j=0; j<num.length()-1; j++) {
                int temp = 0;
                if(arr[j] < arr[j+1]) {
                    temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }  
            }
        }
        
        for(int arrNum : arr) {
            str += String.valueOf(arrNum);
            // System.out.print(arrNum+"\t");
        }
        long answer = Long.parseLong(new String(str));
        return answer;
    }
}
```