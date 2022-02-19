---
layout: post
title: "사이드바 메뉴 설정"
tags: gitblog sidebar menu custom
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 사이드바 메뉴 설정
categories:
    - study
    - blog
related_posts:    
    -    
---
# [gitBlog] 사이드바 메뉴 설정
* 
{:toc}

## 사이드바 메뉴 설정
**_config.yml**의 menu부분 수정   
```yml
menu:
  - title:             About
    url:               /about/
  - title:             Study
    url:               /study/ 
  - title:             Example
    url:               /example/
```
![메뉴 변경](/assets/img/blog/sidebar1.png){:width="80%" height="80%"}
> 사이드바에 메뉴만 추가된 상태라 404가 뜬다.


## 카테고리 메뉴 생성
**_featured_categories**에 .md 파일 생성  


![메뉴 변경](/assets/img/blog/sidebar2.png){:width="50%" height="50%"}   
_featured_categories > example1.md

```yml
layout: list
title: Example1
slug: example1
description: >
  메뉴1 예시
sitemap: false
```
## 각 메뉴에 포스트 넣기
블로그 디렉토리안에 _posts 디렉토리를 만들고 다음과 같이 폴더들을 만든다.   
![메뉴 변경](/assets/img/blog/sidebar4.png){:width="50%" height="50%"}   

example/_posts 안의 예시 포스트들을 각각 example1, example2에 넣고 example 폴더는 삭제한다.
![메뉴 변경](/assets/img/blog/sidebar5.png){:width="50%" height="50%"}   

각 포스트 상단에 다음의 카테고리를 추가해주면  
```yml
categories:
  - example1
```
각 메뉴에 포스트 넣기 성공!  
![메뉴 변경](/assets/img/blog/sidebar6.png){:width="80%" height="80%"}   

## 서브메뉴 만들기
- **_config.yml** 에서 menu부분에 다음과 같이 추가하기    

```yml
menu:
  - title:             About
    url:               /about/
  - title:             Example1
    url:               /example1/
  - title:             Example2
    url:               /example2/
  - title:             Subcategory
    url:               /subCategory/
    submenu:
      -title:         Test1
      -url:           /test1/
      -title:         Test2
      -url:           /test2/
```
- **_featured_categories** 디렉토리에 다음과 같이 subcategory폴더, subcategory.md, test1.md, test2.md 파일들을 생성한다.   
![메뉴 변경](/assets/img/blog/sidebar7.png){:width="50%" height="50%"}   

- 각 .md파일들을 다음과 같이 만들어준다.

```yml
---
layout: list
bigtitle: Subcategory
slug: subcategory
menu: true
submenu: true
description: >
  하위 메뉴 예시
---

# Subcat

## 카테고리

* [Test1]{:.heading.flip-title} --- 테스트 1
* [Test2]{:.heading.flip-title} --- 테스트 2

[Test1]: /test1/
[Test2]: /test2/
```
_featured_categories > subcategory.md
{:.figcaption}

```yml
---
layout: list
category: subcategory
bigtitle: Test1
slug: test1
description: >
  하위메뉴 테스트1

related_posts:
    - 
list: true
order: 1
---
```
_featured_categories > subcategory > test1.md
{:.figcaption}

- _post 폴더에 다음과 같이 디렉토리를 만들어주고 포스트들을 넣어준다.   
![메뉴 변경](/assets/img/blog/sidebar7-1.png){:width="50%" height="50%"}  

각 포스트 상단에 다음의 카테고리를 추가해주면  

```yml
categories:
  - subcategory
  - test1
```
![메뉴 변경](/assets/img/blog/sidebar8.png){:width="70%" height="70%"}   

![메뉴 변경](/assets/img/blog/sidebar9.png){:width="70%" height="70%"}   
서브메뉴 완성!

## 사이드바 커스텀 하기   
_includes > body 폴더와 sidebar-sticky.html 파일을 만들어 다음을 붙여넣는다.

```html
{%raw%}
<div class="sidebar-sticky">
    <div class="sidebar-about" style="margin-bottom: 10px;">

        <!--블로그타이틀-->
        <div class="sidebartitle" style="margin-bottom: 30px;">
            <a class="sidebar-title" href="{{ '/' | relative_url }}">
                <h2 class="h1">{{ site.short_title | default:site.title }}</h2>
            </a>
        </div>
        <!--블로그프로필 이미지-->
        {% if site.logo %}
        <a class="no-hover" style="margin-bottom: 50px;" href="{{ '/' | relative_url }}" tabindex="-1">
            <img src="{% include_cached smart-url url=site.logo %}" class="avatar" alt="{{ site.short_title | default:site.title }}" width="130" height="130" loading="lazy" />
        </a>
        {% endif %}
        <!--블로그 간단한 설명-->
        {% assign text = site.tagline | default:site.description %}
        {% if text %}
        <p class="{% if text.size > 100 %}fine{% endif %}">
            {{ text | markdownify | replace:'<p>','' | replace:'</p>','' }}
        </p>

        {% endif %}
    </div>
    <!--블로그 조회수-->
    <nav class="sidebar-nav heading" role="navigation">
        {% include body/nav.html %}
    </nav>

    <!--소셜바-->
    {% assign author = site.data.authors.first[1] | default:site.author %}
    <div class="sidebar-social">
        {% include components/social.html author=author %}
    </div>

</div>
{%endraw%}
```

각 부분의 순서나 위치를 변경해서 커스텀 할 수 있다.



<br>
<br>

- - -

## Refernce 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)