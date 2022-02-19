---
layout: post
title: "게시글 목차만들기"
tags: gitblog post toc 
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 게시글 목차만들기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [gitBlog] 게시글 목차만들기
* 
{:toc}

### TOC(Table of Contents)
TOC는 H1(`#`)~H6(`######`)의 헤더 목록을 표시해주는 기능이다. Hydejack 테마에서는 TOC를 오른쪽 사이즈 바에 표시해주는 기능을 제공한다.

다음과 같이 포스트의 맨위 제목 다음에 toc를 넣어주자.    
![toc위치](/assets/img/blog/toc1.png){: width="60%" height="60%"}   


TOC(Table Of Content)는 헤딩 태그(`#`~`######`)를 기준으로 생성되므로 문서 작성시 TOC에 표기하고자 하는 문장들은 헤딩태그로 명시 해주어야 한다. 

#### 숫자가 없는 목차 
```markdown
* this unordered seed list will be replaced by the toc
{:toc}
```
![숫자가 없는 목차](/assets/img/blog/toc2.png){: width="50%" height="50%"}    

#### 숫자가 있는 목차 
```markdown
1. this ordered seed list will be replaced by the toc
{:toc}
```
![숫자가 있는 목차 ](/assets/img/blog/toc3.png){: width="50%" height="50%"}   


> ### .large-only
    Hydejack 테마에 적용되어 있는 설정. 화면의 너비가 1665px이상일때에만 목차가 보이도록 한다.
    .large-only가 없으면 포스트의 위쪽으로 목차가 생긴다.
    ```markdown
    * this unordered seed list will be replaced by the toc 
    {:toc .large-only}
    ```


> ### 마크다운 링크를 이용한 목차
 `{:toc}` 를 이용하지 않고 목차를 만들수 있다.
 ```markdown
 [보여줄 텍스트](#링크할 헤더)
 ```
 1. 스페이스바는 '-'로 대체한다
 2. '.', '-', ':'는 무시된다
 3. 대문자는 소문자로 바꿔쓴다
 4. 어떤 헤더든 '#' 하나로 시작한다

 ```
 [1.숫자가 없는 목차](#숫자가-없는-목차)   
 [2.숫자가 있는 목차](#숫자가-있는-목차)   
 ```


<br>
<br>

- - -

### Refernce 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)
- <https://hydejack.com/docs/writing/>
- <https://devinlife.com/howto%20github%20pages/toc-table/>
- <https://velog.io/@jehjong/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EB%B2%95-Markdown-Syntax>