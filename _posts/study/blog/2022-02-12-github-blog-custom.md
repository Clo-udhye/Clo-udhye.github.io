---
layout: post
title: "블로그 테마 커스텀"
tags: gitblog theme custom
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 커스텀
categories:
    - study
    - blog
related_posts:    
    -    
---
# [gitBlog] 블로그 테마 커스텀

### _data > authors.yml
authors.yml의 정보로 게시물을 작성할 때 게시물 마지막에 누가 썼는지 저자를 간단히 소개해준다.

- 이름, 이메일, 소개글을 작성해주자   
```yml
author1:
  name:              Dahye Park
  email:             clo_udhye@naver.com

  about:             
    안녕하세요~ 박다혜입니다!
```

- 프로필 사진을 설정해주자   
assets에 me디렉토리를 생성하고 프로필사진을 넣어준다.   
![저자](/assets/img/blog/authors2.png){:width="30%" height="30%"}    

```yml
picture:
    path:            /assets/me/me.jpg
    # srcset is optional, but can be used to provide higher res versions for retina displays
    srcset:
      1x:            /assets/me/me.jpg
      2x:            /assets/me/me.jpg
```
> `srcset` 설정으로 프로필사진을 모바일에 최적화할 수 있다. 

- sns정보를 작성해주자   

```yml
social:
    #twitter:         <username>
    github:          dev-dahye
    email:           clo_udhye@naver.com
```
> ![다른저자](/assets/img/blog/authors1.png){:width="50%" height="50%"}   
 저자를 추가해서 여러 작성자가 블로그를 관리할수있다. 

### _data > variables.yml 
빠르고 간단하게 foot의 font 크기나 두께, line 높이, 게시물 넓이와 sidebar 넓이 등을 수정할 수 있다.

### _config.yml
전체적인 블로그 설정을 할 수 있다. 
```yml
lang:                  ko-KR, en-US         # 언어
title:                 PMZero               # 블로그 제목
description:           >                    # 소개글
  Dahye의 개발 블로그
tagline:              Dahye의 개발 블로그    # 태그라인
keywords:              [Java, RESTful API]  #블로그를 나타내는 키워드
logo:                  /assets/img/logo.png
author:
  name:                Dahye Park
  email:               clo_udhye@naver.com
```
로고 이미지도 `/assets/img/` 폴더에 넣어주고. 저장하고 서버를 다시 시작해주면 ~    
![로고](/assets/img/blog/config1.png){:width="30%" height="30%"}       
사이드바가 설정이 되었다!


> 줄바꿈을 하고싶은 경우 html <br>태그를 이용하면 된다.
 ```yml
 description:           >                    
  다혜가 만드는 <br> 개발블로그
 ```
 ![긴제목](/assets/img/blog/config3.png){:width="50%" height="50%"}  

Refernce
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)