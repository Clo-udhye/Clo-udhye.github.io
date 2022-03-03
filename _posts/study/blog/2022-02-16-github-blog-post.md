---
layout: post
title: "post 커스텀"
subtitle: post custom
tags: gitblog post about custom
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: post 커스텀
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] post 커스텀
* 
{:toc}

## post 커스텀
### post.html
**_includes > conponents** 디렉토리 생성후 post.html 추가

```html
{% raw %}
{% assign post             = include.post             %}
{% assign no_link_title    = include.no_link_title    %}
{% assign no_excerpt       = include.no_excerpt       %}
{% assign hide_image       = include.hide_image       %}
{% assign hide_description = include.hide_description %}

<article id="post{{ post.id | replace:'/','-' }}" class="page post mb6" role="article">
  <header>
    <!--제목-->
    <h1 class="post-title flip-project-title">
      {% unless no_link_title %}<a href="{{ post.url | relative_url }}" class="flip-title">{% endunless %}
        {{ post.title }}
      {% unless no_link_title %}</a>{% endunless %}
    </h1>
    <!--부제목-->
    <h2 class="post-title flip-project-subtitle">
      {% unless no_link_title %}<a href="{{ post.url | relative_url }}" class="flip-subtitle">{% endunless %}
        {{ post.subtitle }}
      {% unless no_link_title %}</a>{% endunless %}
    </h2>
    <!--카테고리-->
    <div class="post-date">
      {% assign category_start     = "카테고리 : "     | default:" in " %}      <!--카테고리 시작 부분 커스텀-->
      {% assign tag_start          = "해시태그 : #"          | default:" - " %} <!--태그 시작 부분 커스텀-->
      {% assign category_separator = site.data.strings.category_separator | default:">>" %}<!--카테고리 구분자 커스텀-->
      {% assign tag_separator      = " #"     | default:". "  %}<!--태그 구분자 커스텀-->
    
    <span class="ellipis mrl"><!--카테고리, 태그 내용 만들기-->
      {% include components/tag-list.html tags=post.categories meta=site.featured_categories start_with=category_start separator=category_separator %}
      {% include components/tag-list.html tags=post.tags meta=site.featured_tags start_with=tag_start separator=tag_separator %}
      <!--년월일-->
      <br>
      {% assign post_format = "%Y년 %m월 %d일" | default:"%Y %m %d" %}  <!--날짜 관련 커스텀-->
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date:post_format }}</time>
    </span>
    <br>
    </div>
    {% assign alt = false %}
    {% unless hide_image %}{% if post.image %}
      {% unless no_link_title %}<a href="{{ post.url | relative_url }}" class="no-hover no-print-link {% unless post.hide_image %}flip-project{% endunless %}" tabindex="-1">{% endunless %}
        <div class="lead aspect-ratio sixteen-nine flip-project-img"><!--포스트표지 관련 커스텀-->
          {% include_cached components/hy-img.html img=post.image alt=post.title width=864 height=486 %}
        </div>
      {% unless no_link_title %}</a>{% endunless %}
      {% assign alt = '' %}
    {% endif %}{% endunless %}

    {% include components/message.html text=post.description hide=hide_description alt=alt %}
   
  </header>
  <!--post content-->
  <div class="markdown-body">
  {% if no_excerpt %}
    {{ post.content }}
  {% else %}
    {{ post.excerpt }}

    {% capture post_title %}<a class="heading flip-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>{% endcapture %}
    {% assign text = site.data.strings.continue_reading | default:"Continue reading <!--post_title-->" %}
    <!--footer-->
    <footer>
      <p class="read-more">
        {{ text | replace:"<!--post_title-->", post_title }}
      </p>
    </footer>
  {% endif %}
</div>
</article>
{% endraw %}
```
#### tag-list.html 
**_includes > conponents**에 tag-list.html 추가 

```html
{% raw %}
{% assign tags = include.tags %}
{% assign meta = include.meta %}
{% assign start_with = include.start_with %}
{% assign separator = include.separator %}
{% assign end_with = include.end_with %}

{% assign content = '' %}

{% if tags.size > 0 %}
  {% assign content = start_with %}
  {% for tag_slug in tags %}
    {% capture iter_separator %}{% if forloop.last %}{{ end_with }}{% else %}{{ separator }}{% endif %}{% endcapture %}

    {% if major >= 4 and minor >= 1 %}
      {% assign tag = meta | find: "slug", tag_slug %}
    {% else %}
      {% assign tag = meta | where: "slug", tag_slug | first %}
    {% endif %}

    {% if tag %}
      {% capture content_temp %}{{ content }}<a href="{{ tag.url | relative_url }}" class="flip-title">{{ tag.title }}</a>{{ iter_separator }}{% endcapture %}
    {% else %}
      {% capture content_temp %}{{ content }}<span>{{ tag_slug | capitalize }}</span>{{ iter_separator }}{% endcapture %}
    {% endif %}

    {% assign content = content_temp %}
  {% endfor %}
{% endif %}

{{ content }}
{% endraw %}
```


### 포스트 설정과 결과

```yml
layout: post
title: "post 커스텀"
subtitle: post custom
tags: post custom
```

![포스트설정](/assets/img/blog/post1.png){:width="60%" height="60%"}

---

## about 커스텀
### about.html
**_includes > conponents**에 about.html 추가   

```html
{% raw %}
{% assign author = site.data.authors[include.author] | default:site.data.authors.first[1] | default:site.author %}

{% if author.about %}
  <aside class="about related mt4 mb4" role="complementary">
    {% assign about_heading = "작성자" | default:"About" %}<!--About부분의 헤더 텍스트 설정-->
    {% include components/author.html author=author heading=about_heading heading_tag='h1' %}<!--about관련 내용을 가져오는 곳과 헤더 글자크기-->
  </aside>
{% endif %}
{% endraw %}
```

### author.html
**_includes > conponents**에 author.html 추가
```html
{% raw %}
{% assign plugins = site.plugins | default:site.gems %}

<div class="author mt4" style="margin: 10px;">
  {% assign author = include.author %}

  {% assign heading_tag = include.heading_tag | default:'h2' %}
  {% assign heading_id = include.heading_id %}
  <{{ heading_tag }} {% if heading_id %}id="{{ heading_id }}"{% endif %} class="page-title hr-bottom">
    {{ include.heading | default:author.name }}
  </{{ heading_tag }}>

<!--게시물 밑에 작성자 -->
    <!-- 프로필 이미지 -->
        {% if author.picture %}
            {% include_cached components/hy-img.html class="avatar" img=author.picture alt=author.name width="180" height="180" %}  <!--프로필 사진의 크기-->
        {% endif %}
    <!-- 글 --><!--글자의 크기나 색깔-->
    <div class="author-body-description" >
        <span style = " font-size:3em;  color: rgb(0, 0, 0);"><strong>{{ author.name | markdownify }}</strong></span>
        <b style = "font-size:2em; color: rgb(141, 141, 141);">{{ author.about | markdownify }}</b>
    </div>
    <!--소셜-->
    <div class="sidebar-social">
    <div class="sidebar-social">
        {% include components/social.html author=author %}
    </div>
</div>
{% endraw %}
```

#### hy-img.html
**_includes > conponents**에 hy-img.html 추가

```html
{% raw %}
{% assign sources = '' %}
{% if include.img.src or include.img.path %}
  {% assign srcset = null %}

  {% if include.img.srcset %}
    {% capture srcset %}{% for hash in include.img.srcset %}{% assign tmp = hash[1] %}{% include_cached smart-url url=tmp %} {{ hash[0] }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
  {% endif %}

  {% assign src = include.img.src | default:include.img.path %}
  {% capture sources %}
    src="{% include_cached smart-url url=src %}"
    {% if srcset %}srcset="{{ srcset | strip }}"{% endif %}
    {% if include.sizes %}sizes="{{ include.sizes | replace:' ', '' }}"{% endif %}
  {% endcapture %}
{% else %}
  {% capture sources %}
    src="{% include_cached smart-url url=include.img %}"
  {% endcapture %}
{% endif %}
<div class="img-set" style="background-color: rgb(255, 255, 255);"></div>
<img
  {{ sources }}
  {% if include.alt %}alt="{{ include.alt }}"{% endif %}
  {% if include.class %}class="{{ include.class }}"{% endif %}
  {% if include.property %}property="{{ include.property }}"{% endif %}
  {% if include.width and include.height %}loading="lazy"{% endif %}
/>
</div>
{% endraw %}
```

![포스트설정](/assets/img/blog/post2.png){:width="70%" height="70%"}


## 작성자 이미지 커스텀 
브라우저에서 `f12`를 눌러 DevTools를 열고 select element 기능으로 프로필 사진 선택하자
![작성자이미지](/assets/img/blog/post3.png){:width="100%" height="100%"}

선택된 요소의 css를 **_sass > my-style.scss** 아래에 추가.   
같은 방법으로 프로필 옆의 이름과 소개글의 css를 가져와서 수정해주면    
> 수정할 부분에 `!important` 를 넣어줘야 기본 css설정이 아닌 수정된 부분이 반영된다.

```css
.content .avatar {
  float: left !important;
  box-sizing: content-box;
  border: 1rem solid var(--body-bg);
  transition: border-color 1s ease;
  margin-top: 5px !important;
  margin-right: 5px !important;
  width: 140px !important;
  height: 140px !important;
}

.author-body-description {
  margin-left: 200px !important;
  margin-top: 40px !important;
}
```

커스텀이 가능하다!
![작성자이미지](/assets/img/blog/post4.png){:width="100%" height="100%"}


<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)