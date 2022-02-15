---
layout: post
title: "favicon 만들고 적용하기"
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: favicon 만들고 적용하기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [gitBlog] favicon 만들고 적용하기
## favicon 
Favicon이란 Favorite과 Icon의 합성어로 웹 브라우저의 즐겨찾기나 주소창에 뜨는 웹사이트 아이콘

- 다음 웹사이트에 접속해서 사진을 favicon으로 만들 사진을 선택하고 만들기
[https://www.favicon-generator.org/](https://www.favicon-generator.org/)
![favicon-generator](/assets/img/blog/favicon1.png){:width="70%" height="70%"}   

- favicon 다운로드하기
![favicon-generator](/assets/img/blog/favicon2.png){:width="70%" height="70%"}   

- 압축을 풀어 확인해보면 여러 디바이스에 맞는 크기의 이미지들이 생성되어있다.   
assets폴더에 icons폴더를 만들고 `favicon.ico`파일을 옮겨주자.  
![favicon](/assets/img/blog/favicon3.png){:width="70%" height="70%"}   

- _includes > my-head.html에 다음 코드를 삽입한다.   

```html
<link rel="shortcut icon" href="{{ '/assets/icons/favicon.ico'      | relative_url }}">
<link rel="icon" href="{{ '/assets/icons/favicon.ico'      | relative_url }}">
<link rel="apple-touch-icon" href="{{ '/assets/icons/apple-icon-180x180.png' | relative_url }}">
```

- favicon 적용 완료~~   
![favicon](/assets/img/blog/favicon4.png){:width="70%" height="70%"}   

Refernce
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)