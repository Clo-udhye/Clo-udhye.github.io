---
layout: post
title: "블로그 첫화면 / 전체게시글 스타일"
tags: gitblog index post-list
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    블로그 첫화면 / 전체게시글 스타일
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] 블로그 첫화면/전체게시글 스타일
* 
{:toc}

## 블로그 첫화면 About으로 변경
지킬 블로그는 기본 페이지이름이 index로 되어있다. 즉 하고싶은 기본 페이지의 이름을 index로 지으면 된다.
기존의 index.html을 blogs.html로 이름을 바꿔주었다.
![detail](/assets/img/blog/detail1.png){:width="70%" height="70%"}   
> layout이 blog인 페이지로 현재 우리 블로그와 같이 게시물들을 보여주는 페이지이다. 

posts.md은 블로그내의 모든 포스트를 리스트로 보여주는 페이지이다.
posts.md 파일을 카피하고 index.md로 이름을 바꿔주면 기본 시작 페이지가 posts와 같음을 볼수있다.

posts와 blog와 같은 페이지를 그냥 없애기에는 아쉬우니 버튼이나 사이드바의 메뉴로 만들 수 있을 것이다.
![detail](/assets/img/blog/detail2.png){:width="70%" height="70%"}  

다시 새로운 index.md를 작성해보자.
```md
---
layout: about
image: /assets/img/me/me.jpg
description: >
  Java Backend를 공부하고 있습니다.
hide_description: false
---

# About

<!--author-->

<br>

## 소개
---
Github pages 블로그를 운영하는 중입니다.💻  


<div class="me">
    <div><img src= "/assets/img/myBlog/img3.jpg"></div>
    <div><img src= "/assets/img/myBlog/img4.jpg"></div>
    <div><img src= "/assets/img/myBlog/img5.jpg" style="width:100%; height:100%;"></div>
    <div><img src= "/assets/img/myBlog/img6.jpg"></div>
</div>

  <script>
    $(document).ready(function(){
      $('.me').slick();
    });
  </script>

---
```
![detail](/assets/img/blog/detail3.png){:width="70%" height="70%"}  

layout:blog도 그렇고 layout:post 도 그렇고 _layout폴더안에 layout을 커스텀하는 html을 만들어줄수 있다.
layout:about을 커스텀해보자

```html
{% raw %}---
layout: base
---

<article class="page" role="article">
  {% if content contains "<!--author-->" %}
    {% assign plugins = site.plugins | default:site.gems %}
    {% assign author = site.data.authors[page.author] | default:site.data.authors.first[1] | default:site.author %}
    {% capture author_x %}
        <hr>
      {% if author.picture %}
        {% include_cached components/hy-img.html class="avatar" img=author.picture alt=author.name %}
      {% endif %}

      <div class="author-body-description" style="margin-left: 200px; margin-top: 40px;" >
        <span style = "font-size:1.4em;  color: rgb(0, 0, 0);"><strong>{{ author.name | markdownify }}</strong></span>
        <b style = "font-size:0.8em; color: rgb(141, 141, 141);">{{ author.about | markdownify }}</b>
    </div>
    {% endcapture %}
    {% assign content = content | replace:"<!--author-->", author_x %}
  {% endif %}

  <header>
    <h1 class="page-title">{{ page.title }}</h1>
  </header>
  <div class="markdown-body">
  {{ content }}
  </div>
</article>{% endraw %}
```
![detail](/assets/img/blog/detail4.png){:width="70%" height="70%"}   

## 전체 포스트 리스트 스타일 변경   
posts 스타일을 바꿔보자.     
![detail](/assets/img/blog/detail5.png){:width="70%" height="70%"}  

**_includes/components/post-list-item.html** 를 생성하고 다음 코드를 추가

```html
{% raw %}{% assign post = include.post %}
{% assign format = include.format | default:site.data.date_formats.related_post | default:"%Y %m %d" %}

<li class="h6">
  <div>
    <time style="display: inline-block; width: 2.2rem" class="faded fine" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date:format }}</time>
    <a href="{{ post.url | relative_url }}" class="flip-title"><span>{{ post.title }} </span></a>
  </div>
</li>{% endraw %}
```

**_layouts / list.html**  를 생성하고 다음 코드를 추가

```html
{% raw %}---
layout: page
---
<div class="markdown-body">
  {{ content }}
</div>
{% assign posts = site.categories[page.slug] | default:site.tags[page.slug] | default:site.posts %}

{% assign date_formats  = site.data.strings.date_formats               %}
{% assign list_group_by = date_formats.list_group_by | default:"%Y"    %}
{% assign list_entry    = date_formats.list_entry    | default:"%m %d" %}

{% assign prev_date = 0 %}
{% if page.no_groups %}<ul class="related-posts">{% endif %}
<div class="list-post">
{% for post in posts %}
  {% assign current_date = post.date | date:list_group_by %}
  {% unless page.no_groups %}{% if current_date != prev_date %}
    {% unless forloop.first %}</ul>{% endunless %}
    <h2 class="list-lead">{{ current_date }}</h2>
    <ul class="related-posts">
    {% assign prev_date = current_date %}
  {% endif %}{% endunless %}
  {% include_cached components/post-list-item.html post=post format=list_entry %}
  {% if forloop.last %}</ul>{% endif %}
{% endfor %}
</div>{% endraw %}
```
![detail](/assets/img/blog/detail6.png){:width="90%" height="90%"}  

**_sass/my-style.scss**  에 다음 코드를 추가해 세로줄을 만들기

```css
// time-line 목차 리스트
.list-lead{
  margin-bottom: 0 !important;
}
.list-lead::after {
  content:"" !important;
  display:block !important;
  position: relative !important;
  border-radius: 50% !important;
  width: 12px !important;
  height: 12px !important;
  top: -21px !important;
  left: 62px !important;
  // border: 3px solid;

  background-color: lightgrey !important;
  z-index: 1 !important;
}
.list-post li {
  line-height: 3rem !important;
}
.list-post > ul > li:first-child::before, .list-post > ul > li::after{
  content: "" !important;
  width: 4px !important;
  left: 66px !important;
  display: inline-block !important;
  float: left !important;
  position: relative !important;
  background-color: lightgrey !important;
}
.list-post > ul > li > div{
  white-space: nowrap !important;
  overflow: hidden !important;
  text-overflow: ellipsis !important;
}
.list-post > ul > li > div > a{
  margin-left: 1.5rem !important;
  position: relative !important;
}
.list-post > ul > li > div > a::before{
  content: "" !important;
  display: inline-block !important;
  position: relative !important;
  border-radius: 50% !important;
  width: 8px !important;
  height: 8px !important;
  float: left !important;
  top: 1.35rem !important;
  left: 60px !important;
  box-shadow: 0 0 5px 0 grey !important;
  background-color: white !important;
  z-index: 1 !important; 

  transition: all 0.5s !important;
}
.list-post > ul > li > div > a:hover::before{
  background-color: lightgrey !important;
  margin-right: 0.3rem !important;
  box-shadow: 0 0 2px 0 grey !important;
}
.list-post > ul > li:first-child::before{
  height: 3.0rem !important;
  top: -1.5rem !important;
}
.list-post > ul > li:not(:last-child)::after{
  height: 3.3rem !important;
  top: -1.3rem !important;
}
.list-post ul:not(:last-child)>li:last-child::after{
  height: 5.2rem !important;
  top: -1.3rem !important;
}

.list-post .related-posts>li+li{
  margin-top: 0 !important;
}
.list-post li.h6{
  margin-top: 0 !important;
}
```
![detail](/assets/img/blog/detail7.png){:width="90%" height="90%"}  

<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)