---
layout: post
title: "post에 youtube 영상넣기"
tags: gitblog post youtube
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: post에 youtube 영상넣기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [gitBlog] post에 youtube 영상넣기
* 
{:toc}

## youtubePlayer.html 추가
**_includes > youtubePlayer.html** 생성후 다음 코드 삽입

```html
<style>
    .embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; }
    .embed-container iframe,
    .embed-container object,
    .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }
</style>

<div class="embed-container" >
    <iframe src="https://www.youtube.com/embed/{{ include.id }}" frameborder="0" allowfullscreen="" onclick="ga('send', 'event', 'post', 'click', 'youtubePlayer');">
    </iframe>
</div>
```

```
{% raw %}{% include youtubePlayer.html id="Vhr6U9emEbI" %}{% endraw %}
```

id는 원하는 영상 url의 `v=` 뒷부분을 넣는다.   
![youtube](/assets/img/blog/youtube1.png){: width="80%" height="80%"}   


youtube 영상넣기 성공~~!   
{% include youtubePlayer.html id="Vhr6U9emEbI" %}


<br>
<br>

- - -

## Refernce  
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)