---
layout: post
title: "Hits 조회수 보이기"
tags: gitblog hits viewcount
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: Google Analytics로 조회수 보이기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] Hits 조회수 보이기
* 
{:toc}

## 조회수 보이기
깃허브 블로그의 단점은 방문자수나 조회수를 알수 없다는 것이다. 깃허브 블로그의 경우 Jekyll이나 Hugo와 같은 정적 사이트 생성기로 제작되었기 때문에 블로그 방문자와의 상호작용을 기록할 수 없다. 

> 이는 자체적인 백엔드가 없기 때문인데. 그렇다보니 서드파티 서비스를 이용하여 이를 대체하고는 한다. 대표적으로 댓글기능의 경우는 보통 Disqus나 utterances를 이용해서 구현한다. 

## Hits
[HITS](https://hits.seeyoufarm.com/) 에서 커스텀해주고 html 코드를 카피하자
![Hits](/assets/img/blog/hits3.png){: width="80%" heigth="80%"}
![Hits](/assets/img/blog/hits4.png){: width="80%" heigth="80%"}

**_includes > body > sidebar-sticky.html** 에 원하는 순서에 카피해둔 코드를 넣어주자.     
완성~    
![Hits](/assets/img/blog/hits1.png){: width="30%" heigth="30%"}

옆에 화살표가 있는 네모박스가 마음에 안드니 안보이게 바꿔주자   
**_scss > my-style.scss** 에 css 추가하기   

```scss
a.external::after, a::after{
  display: none !important;
}
```
![Hits](/assets/img/blog/hits2.png){: width="30%" heigth="30%"}

<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)