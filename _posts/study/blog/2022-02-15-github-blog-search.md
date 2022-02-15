---
layout: post
title: "검색기능 추가"
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 검색기능 추가
categories:
    - study
    - blog
related_posts:    
    -    
---
# [gitBlog] 검색기능 추가
블로그내에 검색기능을 추가하여 원하는 게시물을 빠르게 찾아보자.
#### 1. 다음 [Github 레파지토리](https://github.com/jekylltools/jekyll-tipue-search)에서 zip 파일을 다운로드 받아 압축을 푼다.

#### 2. **search.html**을 gitBlog폴더 root directory에 붙여넣는다.    
![download/search.html](/assets/img/blog/search1.png){:width="35%" height="35%"}➡️
![gitBlog/search.html](/assets/img/blog/search2.png){:width="40%" height="40%"}
 
#### 3. 다운로드 폴더의 /assets/tipuesearch를 gitBlog/assets/에 붙여넣는다.
![download/assets/tipuesearch](/assets/img/blog/search3.png){:width="40%" height="40%"}➡️
![gitBlog/assets/tipuesearch](/assets/img/blog/search4.png){:width="40%" height="40%"}

#### 4. **_config.yml**에 다음 코드를 추가한다.   
```yaml
tipue_search:
  include:
    pages: false
    collections: []
  exclude:
    files: []
    categories: []
    tags: []
```
include 부분의 pages: false의 설정은 pages 레이아웃에 해당하는 일반 html페이지는 검색하지 않겠다는 것을 의미한다.(포스트 내용 검색에 집중하기 위함)
exclude 부분의 search.html, index.html, tags.html 페이지는 검색에서 제외하겠다는 것을 의미한다.   

#### 5. _includes > body > menu.html 상단메뉴 카테고리들 밑에 아래코드를 추가한다.   

```html
<!--검색 tipuesearch -->
<div class="nav-span">
    <form action="/search">
        <div class="tipue_search_left">
            <img src="/assets/tipuesearch/search.png" class="tipue_search_icon">
        </div>
        <div class="tipue_search_right">
            <input type="text" name="q" id="tipue_search_input" pattern=".{1,}" title="At least 1 characters" required>
        </div>
        <div style="clear: both;"></div>
    </form>
</div>
```

#### 6. include > my-head.html 가장 아래에 다음의 코드를 추가한다.   

```html
<!-- tipuesearch -->
<link rel="stylesheet" href="/assets/tipuesearch/css/tipuesearch.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script src="/assets/tipuesearch/tipuesearch_content.js"></script>
<script src="/assets/tipuesearch/tipuesearch_set.js"></script>
<script src="/assets/tipuesearch/tipuesearch.min.js"></script>
```

#### 7. 서버를 시작하면 검색창 생성되었다!   
![검색창](/assets/img/blog/search5.png){:width="90%" height="90%"}

#### 8. 검색창 꾸미기
- _sass>my-style.scss 에 다음 코드 추가, 탑메뉴바가 너무 넓어서 높이를 줄이자.

```css
.nav-btn-bar{
  height: 3rem;
}
```

- assets>tipuesearch > css > tipuesearch.css #tipue_search_input에서 다음과 같이 수정

```css
#tipue_search_input
{
     color: #333;
     max-width: 150px;		    /*최대 넓이 줄이고*/
     max-height: 20px;		    /* 높이 지정*/
     padding: 15px;			    /* 패딩 줄이기*/
     border: 2px solid #626591;	/* 굵게, 테두리는 색 바꾸기*/
     border-radius: 0;
     -moz-appearance: none;
     -webkit-appearance: none;
     box-shadow: none;
     outline: 0;
     margin: 0;
     text-align: center;		/*텍스트 중간에 오게하기*/
}

/* 돋보기 아이콘 위치 수정*/
.tipue_search_icon
{
     width: 19px;
     height: 19px;
     margin-bottom: 1rem;
}

/* 검색창 위치 조정*/
.tipue_search_left
{
     float: left;
     padding: 10px 5px 0 0;
     color: #170247;
     max-height: 20px;
}
```

Refernce
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)