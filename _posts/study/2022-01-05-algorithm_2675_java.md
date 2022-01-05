---
layout: post
title:  "백준 알고리즘 2675번 #JAVA"
subtitle: "백준 알고리즘 2675번"
categories: study
tags: algorithm
comments: true
---


## 01. 문제 설명

> 문자열 S를 입력받은 후에, 각 문자를 R번 반복해 새 문자열 P를 만든 후 출력하는 프로그램을 작성하시오.  
> 즉, 첫 번째 문자를 R번 반복하고, 두 번째 문자를 R번 반복하는 식으로 P를 만들면 된다. S에는 QR Code "alphanumeric" 문자만 들어있다.  
> QR Code "alphanumeric" 문자는 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ\$%*+-./: 이다.  
  
> <b>입력 : </b>첫째 줄에 테스트 케이스의 개수 T(1 ≤ T ≤ 1,000)가 주어진다. 각 테스트 케이스는 반복 횟수 R(1 ≤ R ≤ 8), 문자열 S가 공백으로 구분되어 주어진다.  
> S의 길이는 적어도 1이며, 20글자를 넘지 않는다.  
  
> <b>출력 : </b>각 테스트 케이스에 대해 P를 출력한다.  

## 02. 문제 풀이
#### -케이스 전체 개수인 T를 입력받고 T번 반복하는동안 S 문자열, 그 문자열의 문자들을 반복 출력할 R을 입력받아 for문을 통해 출력한다.

```JAVA
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        try (BufferedReader bf = new BufferedReader(new InputStreamReader(System.in))) {
            int T = Integer.parseInt(bf.readLine());
            StringTokenizer st;
            for(int i=0; i<T; i++) {
                st = new StringTokenizer(bf.readLine()," ");
                int R = Integer.parseInt(st.nextToken()); // 반복할 횟수
                String S = st.nextToken(); // 문자열

                for(int j=0; j<S.length(); j++) {
                    for(int k=0; k<R; k++) {
                        System.out.print(S.charAt(j));
                    }
                }
                System.out.println();
            }     
        }
    }
}
```