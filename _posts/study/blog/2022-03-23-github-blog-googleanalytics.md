---
layout: post
title: "Google Analytics 블로그 통계 확인하기"
tags: gitblog googleanalytics viewcount
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: Google Analytics 블로그 통계 확인하기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] Google Analytics 블로그 통계 확인하기
* 
{:toc}

## [Google Analytics](https://analytics.google.com/analytics/web/?hl=ko)
- 구글 애널리틱스에 접속해서 측정시작을 누른다.   
![google_analytics](/assets/img/blog/google_analytics1.png){:width="100%" height="100%"}  
 
- 설정을 해준다.   
![google_analytics](/assets/img/blog/google_analytics2.png){:width="80%" height="80%"}   
![google_analytics](/assets/img/blog/google_analytics3.png){:width="80%" height="80%"}   

- 동의하고 만들기
![google_analytics](/assets/img/blog/google_analytics4.png){:width="100%" height="100%"}   

![google_analytics](/assets/img/blog/google_analytics5.png){:width="100%" height="100%"}   

- 웹 스트림 생성
![google_analytics](/assets/img/blog/google_analytics6.png){:width="100%" height="100%"}   
![google_analytics](/assets/img/blog/google_analytics7.png){:width="100%" height="100%"} 

- 측정ID를 **_config.yml**에 등록
![google_analytics](/assets/img/blog/google_analytics8.png){:width="100%" height="100%"}   
![google_analytics](/assets/img/blog/google_analytics9.png){:width="100%" height="100%"}  

- 새로운 온페이지 태그를 **_includes>analytics.html**을 만들고 추가
![google_analytics](/assets/img/blog/google_analytics10.png){:width="100%" height="100%"}   
![google_analytics](/assets/img/blog/google_analytics11.png){:width="100%" height="100%"} 

- **_layout>post.html**에 analytics.html 추가
![google_analytics](/assets/img/blog/google_analytics12.png){:width="100%" height="100%"}   

- 통계확인하기
![google_analytics](/assets/img/blog/google_analytics13.png){:width="100%" height="100%"}   



<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)