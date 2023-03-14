---
layout: post
title:  "머스테치(Mustache) 한글 깨짐"
subtitle: "머스테치(Mustache) 한글 깨짐"
categories: study
tags: Spring
comments: true
---

스프링 부트와 AWS로 혼자 구현하는 웹 서비스를 기반으로 INDEX 화면을 띄우는데 INDEX의 한글 깨짐 현상이 발생했다.  
구글링 해보니 `스프링부트 2.7.0` 버전에서 mustache 한글 깨짐 이슈가 있다고 한다.


## 해결 방법-1
`build.gradle` 에서 스프링부트 버전을 2.6.x 으로 변경
(2.6.8 또는 2.6.7 버전 사용)  
```
plugins {
	id 'org.springframework.boot' version '2.6.7'
}
```

## 해결 방법-2
`application.properties` 에 인코딩 설정 추가  
```
server.servlet.encoding.force-response= true
```

