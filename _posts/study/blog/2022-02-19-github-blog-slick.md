---
layout: post
title: "Slick 슬라이드 게시글 만들기"
tags: gitblog post slide slick
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: Slick을 이용한 슬라이드 게시글 만들기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] Slick 슬라이드 게시글 만들기
* 
{:toc}

## 슬라이드 게시글 만들기
1. <https://kenwheeler.github.io/slick/> 접속해서 `get it now` -> `download now`, 압축풀기   
2. 블로그 디렉토리의 assets폴더에 css 폴더를 만들고 다운로드된 폴더안의 slick폴더를 넣는다.   
![다운로드된 폴더](/assets/img/blog/slick1.png){:width="50%" height="50%"}   
![블로그 폴더](/assets/img/blog/slick2.png){:width="50%" height="50%"}   

3. _includes > my-head.html 의 tipueseach아래에 다음 코드를 삽입한다.

```markdown
<!--slick-->
<link rel="stylesheet" type="text/css" href="/assets/css/slick/slick.css"/>
<link rel="stylesheet" type="text/css" href="/assets/css/slick/slick-theme.css"/>
<!-- 이부분은 tipuesearch와 버전충돌이 일어나서 제외 시켰다.-->
<!--<script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>-->
<script type="text/javascript" src="/assets/css/slick/slick.min.js"></script>
```

4. 게시글에 다음 코드를 추가

```html
<div class="main_center">
    <div><img src= "/assets/img/blog/slickExample1.jpg" style="width: auto; height: 500px;"></div>
    <div><img src= "/assets/img/blog/slickExample2.jpg" style="width: auto; height: 500px;"></div>
    <div><img src= "/assets/img/blog/slickExample3.jpg" style="width: auto; height: 500px;"></div>
</div>
<script>
    $(document).ready(function() {
        $('.main_center').slick({
            autoplay : true, /*자동으로 슬라이딩됨*/
            dots : true, /* 하단 점 버튼 */
            speed : 300 /* 이미지가 슬라이딩시 걸리는 시간 */,
            infinite : true,
            autoplaySpeed : 30000 /* 이미지가 다른 이미지로 넘어 갈때의 텀 */,
            arrows : true,
            slidesToShow : 1,
            slidesToScroll : 1,
            touchMove : true, /* 마우스 클릭으로 끌어서 슬라이딩 가능여부 */
            nextArrows : true, /* 넥스트버튼 */
            prevArrows : true,
            arrow : true, /*false면 좌우 버튼 없음, true면 좌우 버튼 보임*/
            fade : false
        });
    });
</script>
```

<div class="main_center">
    <div><img src= "/assets/img/blog/slickExample1.jpg" style="width: auto; height: 500px;"></div>
    <div><img src= "/assets/img/blog/slickExample2.jpg" style="width: auto; height: 500px;"></div>
    <div><img src= "/assets/img/blog/slickExample3.jpg" style="width: auto; height: 500px;"></div>
</div>
<script>
    $(document).ready(function() {
        $('.main_center').slick({
            autoplay : true, 
            dots : true, 
            speed : 300, 
            infinite : true,
            autoplaySpeed : 30000,
            arrows : true,
            slidesToShow : 1,
            slidesToScroll : 1,
            touchMove : true, 
            nextArrows : true, 
            prevArrows : true,
            arrow : true, 
            fade : false
        });
    });
</script>

> #### 슬라이드 버튼 커스텀
 <a href="/assets/css/slick/icon.zip" download>🖇️icon.zip</a>    
 왼쪽 오른쪽 버튼 이미지를 assets > css > slick 에 넣는다.
 이미지를 url을 slick-theme.css와 같은 위치에 넣는다.
 ```
 slick-theme.css 에서 91번째 줄 content : url(left.png);
 95번째 줄 content : url(right.png);
 109번째 줄 content : url(right.png); , 113번째 줄 역시 content : url(left.png);
 ```


<br>
<br>

- - -

## Refernce 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)