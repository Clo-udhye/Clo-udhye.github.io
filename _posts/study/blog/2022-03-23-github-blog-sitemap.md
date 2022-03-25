---
layout: post
title: "검색엔진 최적화 - 검색시 블로그 노출하기"
tags: gitblog sitemap rss robots
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 검색엔진 최적화 - 검색시 블로그 노출하기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] 검색엔진 최적화 - 검색시 블로그 노출하기
* 
{:toc}

## 검색엔진 최적화
검색엔진최적화는 검색엔진이 이해하기 쉽도록 홈페이지 구조를 설정하여 포털 사이트 상위에 노출시키는 작업이다.
jekyll으로 제작된 깃허브 블로그에 SEO 작업을 진행한다.

## Sitemap
- 웹 크롤링 로봇이 이용할 수 있는 웹사이트의 접근 가능한 페이지의 목록
- 사이트맵을 등록하면 구글에서 주기적으로 크롤링을 한 뒤 관련 검색어로 검색 시 해당 사이트가 노출이 된다.
- sitemap.xml 파일을 사용하면 사이트 구조를 구글, 네이버, 다음 등 검색엔진에 손 쉽게 제출할 수 있다.
- 검색엔진에 크롤링해야하는 URL을 알려줌으로써 색인을 생성하는 방법을 제안한다.

root 경로에 **sitemap.xml** 파일을 만든다.
```xml
{% raw %}---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd" xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {% for post in site.posts %}
    <url>
      <loc>{{ site.url }}{{ post.url }}</loc>
      {% if post.lastmod == null %}
        <lastmod>{{ post.date | date_to_xmlschema }}</lastmod>
      {% else %}
        <lastmod>{{ post.lastmod | date_to_xmlschema }}</lastmod>
      {% endif %}

      {% if post.sitemap.changefreq == null %}
        <changefreq>weekly</changefreq>
      {% else %}
        <changefreq>{{ post.sitemap.changefreq }}</changefreq>
      {% endif %}

      {% if post.sitemap.priority == null %}
          <priority>1.0</priority>
      {% else %}
        <priority>{{ post.sitemap.priority }}</priority>
      {% endif %}

    </url>
  {% endfor %}
</urlset>{% endraw %}
```
- 해당 파일을 커밋, 푸쉬 한다.
- 블로그 주소/sitemap.xml 에 들어가서 제대로 사이트맵이 등록되었는지 확인해 본다.
- 홈페이지의 모든글의 정보를 담고있는 사이트맵이 출력되는 것을 알 수 있다. 추후에 블로그 포스팅을 푸쉬 하면 jekyll이 빌드하면서 사이트맵도 자동으로 갱신된다.
- Gemfile파일에 gem ‘jekyll-sitemap’이 있는것을 확인해보고 있다면 자동으로 갱신된다.
(참고로 /sitemap.xml을 실행했을 때 제대로 안 나오는 경우가 있는데, 주소 링크에 특수문자가 들어간 경우이다. 깃허브 블로그의 경우 포스팅 파일명으로 링크가 생성되므로 포스팅 파일명은 특수문자 및 한글 사용을 안 하도록 한다.)

![sitemap](/assets/img/blog/sitemap1.png){:width="90%" height="90%"}   

## RSS
- RSS(Rich Site Summary)란 뉴스나 블로그 사이트에서 주로 사용하는 콘텐츠 표현 방식이며, 웹 사이트 관리자는 RSS 형식으로 웹 사이트 내용을 보여 준다.
- RSS피드는 정기적으로 업데이트 되는 웹 콘텐츠를 전달해 주는 형태이며, 글의 전체 혹은 요약된 정보와 작성자 등의 정보가 포함되어 있다. 즉 블로그의 글을 작성하면 RSS피드에도 전달이 되고, 구글, 네이버, 다음 등을 통해 글을 검색하면, 검색 엔진은 블로그의 RSS피드로부터 글을 받게 되어 해당 블로그로 들어오게 된다.

root 경로에 **feed.xml** 파일을 만든다.
```xml
{% raw %}---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
  <channel>
    <title>{{ site.title | xml_escape }}</title>
    <description>{{ site.description | xml_escape }}</description>
    <link>{{ site.url }}{{ site.baseurl }}/</link>
    <atom:link href="{{ '/feed.xml' | prepend: site.baseurl | prepend: site.url }}" rel="self" type="application/rss+xml"/>
    <pubDate>{{ site.time | date_to_rfc822 }}</pubDate>
    <lastBuildDate>{{ site.time | date_to_rfc822 }}</lastBuildDate>
    <generator>Jekyll v{{ jekyll.version }}</generator>
    {% for post in site.posts limit:30 %}
      <item>
        <title>{{ post.title | xml_escape }}</title>
        <description>{{ post.content | xml_escape }}</description>
        <pubDate>{{ post.date | date_to_rfc822 }}</pubDate>
        <link>{{ post.url | prepend: site.baseurl | prepend: site.url }}</link>
        <guid isPermaLink="true">{{ post.url | prepend: site.baseurl | prepend: site.url }}</guid>
        {% for tag in post.tags %}
        <category>{{ tag | xml_escape }}</category>
        {% endfor %}
        {% for cat in post.categories %}
        <category>{{ cat | xml_escape }}</category>
        {% endfor %}
      </item>
    {% endfor %}
  </channel>
</rss>{% endraw %}
```
해당 파일을 커밋, 푸쉬 하고 블로그 주소/feed.xml 에 제대로 등록되었는지 확인해 본다.
![sitemap](/assets/img/blog/sitemap2.png){:width="90%" height="90%"}   

## Robots
robots.txt 또는 robots.xml은 로봇 배제 표준을 따르는 일반 텍스트 파일이다.   
쉽게 표현하면 검색 엔진이 해당 사이트의 콘텐츠를 가져가는것을 허락하는 설정과 가져가면 안되는 설정을 하는 부분이라고 보면 된다.

root 경로에 **robots.xml** 파일을 만든다.
```xml
User-agent: *
Allow: /

Sitemap: http://dev-dahye.github.io/sitemap.xml
```

>User-agent는 허용할 검색엔진 명을 넣게 된다. 따로 설정하지 않으면(*) 모든 검색엔진을 허용하게 된다.
 Sitemap은 본인 블로그 사이트맵 주소를 넣어 주면 된다.

```xml
// 모든 웹사이트 콘텐츠에 대한 모든 웹 클롤러의 접근을 차단
User-agent: *
Disallow: /

//만약 구글 로봇만 차단시키고 싶다면 User-//agent에 * 부분을 Googlebot으로 변경하여 설정
User-agent: Yeti
Disallow: /hello/

//이렇게 설정하면 웹사이트의 모든 콘텐츠의 네이버 검색로봇(Yeti)의 크롤링을 허용하되, /hello/ 디렉토리 안의 페이지에 대한 접근만 차단한다는 의미
```

## 블로그 등록
### [Google Search Console](https://search.google.com/search-console/welcome?hl=ko)
Google Search Console에 접속한다. SEARCH CONSOLE 버튼을 클릭한다.    
- 시작하기 버튼을 누른다.  
![sitemap](/assets/img/blog/sitemap3.png){:width="80%" height="80%"}     

- URL 접두어에 자신의 깃헙블로그 주소를 넣는다.   
![sitemap](/assets/img/blog/sitemap4.png){:width="80%" height="80%"}     

- html 파일을 다운받아 깃허브블로그 코드 폴더 root에 넣는다.   
![sitemap](/assets/img/blog/sitemap5.png){:width="80%" height="80%"}     
![sitemap](/assets/img/blog/sitemap6.png){:width="80%" height="80%"}     

- 소유권 확인과정을 거친다.   
![sitemap](/assets/img/blog/sitemap7.png){:width="80%" height="80%"}   

- 속성으로 이동해서 sitemaps 메뉴 > sitemap.xml을 입력하고 제출 버튼을 누른다.   
![sitemap](/assets/img/blog/sitemap8.png){:width="80%" height="80%"}   

### [네이버 서치어드바이저](https://searchadvisor.naver.com/)
- 네이버 서치어드바이저에 접속 한다.
![sitemap](/assets/img/blog/sitemap9.png){:width="80%" height="80%"}   

- 로그인후 웹마스터 도구에서 블로그 주소를 등록해 사이트를 추가해 준다.   
![sitemap](/assets/img/blog/sitemap10.png){:width="80%" height="80%"}   

- 웹마스터 도구에서 제공하는 html 파일을 다운받아 본인 블로그에 업로드하거나 메타태그를 이용하는 방법으로 사이트 소유권을 확인한다.   
![sitemap](/assets/img/blog/sitemap11.png){:width="80%" height="80%"}   
![sitemap](/assets/img/blog/sitemap12.png){:width="80%" height="80%"}   
![sitemap](/assets/img/blog/sitemap13.png){:width="80%" height="80%"}   

- 왼쪽 요청 메뉴로 들어가 사이트맵을 제출해준다.
![sitemap](/assets/img/blog/sitemap14.png){:width="80%" height="80%"}   

깃허브에서 공식적으로 지원하는 jekyll블로그는 RSS2.0이 아닌, ATOM이라는 방식으로 feed.xml을 생산해준다.
그리고 ATOM방식으로 제작된 피드는 네이버 웹마스터도구에 등록이 안된다.




<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)