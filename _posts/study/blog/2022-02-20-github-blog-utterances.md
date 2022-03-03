---
layout: post
title: "Utterances 댓글 기능 추가"
tags: gitblog comment utterances
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: Utterances를 이용한 댓글 기능 추가
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] Utterances 댓글 기능 추가
* 
{:toc}

## Utterances란
utterances는 깃헙 계정이있고 본인 컴퓨터에 깃헙을 로그인 저장되어있다면 버튼 하나로 손쉽게 댓글을 쓸 수 있다. 

utterances는 깃허브의 이슈기능을 가지고 댓글을 생성해준다. 게시글 하나가 이슈 하나와 매핑이 되고, 게시글에 댓글을 달면 해당 이슈에 댓글이 달린다. 

댓글 창은 iframe으로 동작하며 해당 페이지가 로드 될 때, 페이지의 URL, pathname, 혹은 title을 가지고 issue search API를 통해 해당 이슈에 달린 댓글을 로딩하여 댓글 창에 로딩시켜준다.

만약에 내가 최초로 댓글을 달아서 이슈가 없다면 utterances-bot이 자동적으로 이슈를 생성해준다.

### Utterances 장점
✔️ 깃허브는 다수 개발자가 가입은 해둔 플랫폼입니다.   
깃허브 앱인 utterances는 깃허브 계정만 있으면 되기 때문에 블로그 운영자와 사용자는 대부분 별도 가입을 하지 않아도 됩니다.

✔️ 특별한 관리 부담이 필요치 않습니다.   
운영자 입장에서도 자주 사용하는 플랫폼인 깃허브는 친숙한 환경이기에 설치나 관리에 대한 부담이 없습니다.

✔️ 댓글 알림을 받을 수 있습니다.   
github issues를 댓글 쓰레드로 사용하는 utterances는 댓글이 등록되면, 즉 새로운 issue가 등록된 것이므로 메일 알림을 받을 수 있습니다.

✔️ 설치 및 설정이 쉽습니다.   
utterances앱을 깃허브 계정에 추가한 뒤 댓글 저장 용도로 사용될 신규 레포지토리 추가하여 권한을 주면 됩니다. 이후 댓글 영역에 스크립트 코드 한 줄만 추가해주면 셋팅이 끝납니다.

✔️ Markdown 문법을 이용하여 댓글 작성이 가능합니다.   
github 플랫폼을 이용하기 때문에 당연히 마크다운 문법 사용이 가능합니다.

## 댓글 저장소 만들기
먼저 댓글있을 저장소(레파지토리)를 지정해야합니다. 따라서 새로운 레파지토리를 만들어줍니다. 
![저장소](/assets/img/blog/comment1.png){: width="70%" height="70%"}   

## Utterances 설치하기
- [utterances](https://utteranc.es/)에서 앱을 설치하자. `Configuration`의 `utterance app`클릭 > `Install` 클릭   
![utterances](/assets/img/blog/comment2.png){: width="70%" height="70%"}  
![utterances](/assets/img/blog/comment3.png){: width="70%" height="70%"}   

- 다음과 같이 설정해주고 `Install`   
![utterances](/assets/img/blog/comment4.png){: width="50%" height="50%"}   

- 깃헙아이디/저장소이름 : `dev-dahye/blog-comment-repo`       
![utterances](/assets/img/blog/comment5.png){: width="70%" height="70%"}   

- 게시글과 레파지토리의 이슈를 매핑하는 방법을 선택(post <– –> issue 매핑)
![저장소](/assets/img/blog/comment6.png){: width="70%" height="70%"}   
1. pathname     
    포스트의 pathname으로 이슈를 생성한다.       
2. page URL     
    게시글의 URL 전체로 이슈를 매핑한다.    
3. page title     
    게시글의 제목으로 이슈를 매핑한다.    
4. issue number      
    이슈 번호를 가지고 매핑한다.     
5. issue title contains specific term      
    게시글 제목에 특정 단어가 들어가 있는지 체크하여 매핑한다.

- Theme 와 Enable Utterances
어떤 테마를 적용할지 골라주고 코드를 복사해주자.
![저장소](/assets/img/blog/comment7.png){: width="70%" height="70%"}   

- **_includes > my-comments.html** 을 만들고 복사 해뒀던 코드를 붙여넣기, `<aside>` 태그를 추가해서 댓글부분의 소제목을 추가해주자.

```html
<aside class="comments" role="complementary">
    <h2>Comments</h2>
    <hr/>
    <!--repo=           “레포주소”
        issue-term=     “방식”
        theme=          “테마”-->
    <script src="https://utteranc.es/client.js"
        repo="dev-dahye/blog-comment-repo"
        issue-term="url"
        theme="github-light"
        crossorigin="anonymous"
        async>
    </script>
</aside>
```
- **_layouts > post.html** 폴더와 파일을 만들어주고 다음 코드를 넣어 포스트의 레이아웃을 설정해주자.   

```html
{%raw%}
---
layout: base
---

{% include_cached components/post.html post=page no_link_title=true no_excerpt=true hide_image=page.hide_image hide_description=page.hide_description %}

<!-- list layout -->
{% if page.list %}
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

      <!-- id="{{ list_group_by | slugify }}-{{ current_date | slugify }}" -->
  <h2 class="list-lead">{{ current_date }}</h2>
    <ul class="related-posts">
      {% assign prev_date = current_date %}
    {% endif %}{% endunless %}
    {% include_cached components/post-list-item2.html post=post format=list_entry %}
    {% if forloop.last %}</ul>{% endif %}
  {% endfor %}
  </div>
{% endif %}

{% assign addons = page.addons | default:site.hydejack.post_addons %}
{% unless addons %}{% assign addons = "about,newsletter,related,random" | split:"," %}{% endunless %}

<!-- <script>console.log("{{addons}}"); console.log("{{page.addons}}"); console.log("{{site.hydejack.post_addons}}")</script> -->
{% for addon in addons %}
  {% case addon %}
  {% when 'about' %}
    {% include_cached components/about.html author=page.author %}
  {% when 'related' %}
    {% include components/related-posts.html %}
  {% when 'comments' %}
    {% include my-comments.html %}      <!--댓글 부분-->
  {% else %}
  {% endcase %}
{% endfor %}
{%endraw%}
```

##  댓글 기능 추가 완료  
![저장소](/assets/img/blog/comment8.png){: width="80%" height="80%"}

- 댓글을 달면 댓글저장소에 이슈가 생성되고 댓글이 달린다.   
![저장소](/assets/img/blog/comment9.png){: width="80%" height="80%"}
![저장소](/assets/img/blog/comment9-1.png){: width="80%" height="80%"}

<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)