---
layout: post
title: "footer 설정하기"
tags: gitblog footer custom
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: footer 설정하기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] footer 설정하기
* 
{:toc}

## footer 설정
#### 1. html 추가
**_includes > body** 에 footer.html 추가

```html
{% if site.copyright.size > 0 or site.legal.size > 0 or site.hydejack.advertise %}
    <footer class="content" role="contentinfo">
    <hr/>
    {% if site.copyright.size > 0 %}
        <p><small class="copyright">{{ site.copyright | markdownify | replace:'<p>','' | replace:'</p>','' }}</small></p>
    {% endif %}

    <p><small>----------Powered by Hydejack----------</p> <p><span id="_version">Dahye의 개발블로그</span></small></p>
    <hr class="sr-only"/>
    </footer>
{% endif %}
```

footer 설정 완료!   
![footer](/assets/img/blog/footer1.png){:width="80%" height="80%"}   

<br>
<br>

- - -

## Reference 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)