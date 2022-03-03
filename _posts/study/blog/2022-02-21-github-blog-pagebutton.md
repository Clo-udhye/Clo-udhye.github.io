---
layout: post
title: "이전글/다음글 기능 추가하기"
tags: gitblog page pagebutton
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 이전글/다음글 기능 추가하기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] 이전글/다음글 기능 추가하기
* 
{:toc}

### `_includes` 폴더 정리
기능을 추가하기전에 `_includes` 폴더를 정리 해주었습니다.
- my-comments.html 을 components > comment.html 로 이동 및 이름 수정
- _layouts > post.html 을 다음과 같이 수정 

```html
{%raw%}
---
layout: base
---
{% include_cached components/post.html post=page no_link_title=true no_excerpt=true hide_image=page.hide_image hide_description=page.hide_description %}
{% include_cached components/about.html author=page.author %}
{% include components/related-posts.html %}
{% include components/comments.html %}
{%endraw%}
```
- youtubePlayer.html 을 components > youtubePlayer.html 로 이동
- youtubePlayer를 사용했던 포스트에서 path 수정

```html
{%raw%}{% include components/youtubePlayer.html id="Vhr6U9emEbI" %}{%endraw%}
```

## 버튼 추가
**_includes > components > page-button.html** 생성

```html
{%raw%}
<div class="page-control">
    {% if page.previous.url %}
    <a class="button" href="{{ page.previous.url }}">
        <div class="previous-page">
            <span>이전글</span>
            <p>{{ page.previous.title }}</p>
        </div>
    </a>
    {% else %}
    <a style="pointer-events:none; cursor: default;"><div class="previous-page"><span></span><p></p></div></a>
    {% endif %}
    {% if page.next.url %}
    <a class="button" href="{{ page.next.url }}">
        <div class="next-page">
            <span>다음글</span>
            <p>{{ page.next.title }}</p>
        </div>
    </a>
    {% else %}
    <a style="pointer-events:none; cursor: default;"><div class="next-page"><span></span><p></p></div></a>
    {% endif %}
</div>
{%endraw%}
```

**_layouts > post.html** 에 원하는 순서에 다음 코드삽입    
```html
{%raw%}{% include components/page-button.html %}{%endraw%}
```

버튼 생성 완료   
![페이지 버튼](/assets/img/blog/pageButtton1.png){: width="80%" height="80%"}

## 버튼 디자인
**_scss > my-style.scss** 에 css 추가

```css
.page-control {
  line-height: 1.15;
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
  display: flex;
  height: 150px;
  margin-bottom: 100px;
}
.page-control > a {
  width: 50%;
  text-decoration: none;
}
.button:hover {
  background:linear-gradient(to bottom, #f6f6f6 5%, #ffffff 100%);
  background-color:#f6f6f6;
}
.previous-page{
  width: 100%;
  display: flex;
  flex-direction: column;
  row-gap: 25px;
  padding: 20px;
  cursor: pointer;
}
.previous-page > span{
  font-size: 1rem;
  line-height: 28px;
  font-weight: 500;
}
.previous-page> p{
  white-space: pre-wrap;
  font-size: 20px;
  line-height: 34px;
  font-weight: 300;
}
.next-page{
  width: 100%;
  display: flex;
  flex-direction: column;
  row-gap: 25px;
  padding: 20px;
  cursor: pointer;
  text-align: right;
}
.next-page > span{
  text-align: right;
  font-size: 1rem;
  line-height: 28px;
  font-weight: 500;
}
.next-page> p{
  white-space: pre-wrap;
  font-size: 20px;
  line-height: 34px;
  font-weight: 300;
}
```

디자인 커스텀 완료   
![페이지 디자인](/assets/img/blog/pageButtton2.png){: width="80%" height="80%"}

<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)