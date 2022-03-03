---
layout: post
title: "반응형 블로그 - 검색창"
tags: gitblog mobile search responsive-web
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 반응형 블로그 - 검색창
categories:
    - study
    - blog
related_posts:    
    - /study/blog/2022-02-15-github-blog-topmenubar/  
---
# [Blog] 반응형 블로그 - 검색창
* 
{:toc}

## 검색창
모바일 화면에서 탑메뉴바의 검색창이 이상하게 보이는 오류를 발견했다.   
>브라우저에서 `F12`를 눌러서 개발자 도구를 켜고 `device toolbar` 버튼을 누르면 웹화면에서도 화면 크기를 조절해서 볼수있다!

![모바일 화면](/assets/img/blog/mobile1.png){: width="70%" height="70%"}   

반응형 css를 적용해서 모바일에서도 예쁘게 블로그가 보이도록 만들어보자! 모바일 화면에서는 검색창은 숨기고 아이콘을 누르면 검색페이지로 갈수있도록 만들것이다. 

### 화면 크키에 맞는 css적용
반응형 웹페이지를 만들때는, CSS를 각 크기에 맞게 파일을 만들어 주고, 기본html인 index.html의 head에 버전별로 적용해준다. 현재는 하나의 css파일을 이용해서 웹과 모바일 화면을 보여주고 있다!   

**_includes > my-head.html 의 tipuesearch**   
```html
<!-- tipuesearch -->
<link rel="stylesheet" href="/assets/tipuesearch/css/tipuesearch.css">
```

적용할 css를 불러오는 `<link>` 태그에 `media` 속성을 추가해서 화면의 크기에 맞는 css 파일을 불러오도록 수정해주자.
> `max-width`값으로 화면의 너비를 조절해줄 수 있다. 너비가 언제일때부터 모양이 이상해지는지 체크해서 설정해주었다.

```html
<!-- tipuesearch -->
<link rel="stylesheet" href="/assets/tipuesearch/css/tipuesearch.css" media="all and (max-width:2000px)">
<link rel="stylesheet" href="/assets/tipuesearch/css/tipuesearch-mobile.css" media="all and (max-width:510px)">
```

### css 수정하기
**assets > tipuesearch > css > tipuesearch-mobile.css**    
기존에 있던 tipuesearch.css 파일을 복사해서 tipuesearch-mobile.css 라는 css파일을 만들어주었다.
화면의 너비가 작아지면 검색창이 없어지도록 `#tipue_search_input`을 수정해준다.

```css
/* search box */
#tipue_search_input{
    display: none;
}
```
![검색창 안보이기](/assets/img/blog/mobile3.png){: width="50%" height="50%"}   

아이콘의 크기와 위치도 맞게 수정해주자!
```css
.tipue_search_icon
{
     width: 35px;
     height: 35px;
     margin-bottom: 1rem;
}

.tipue_search_left
{
     float: left;
     padding: 10px 5px 0 0;
     color: #170247;
     max-height: 50px;
}
```
![아이콘수정](/assets/img/blog/mobile4.png){: width="50%" height="50%"}   

### 검색페이지로 이동
아이콘을 누르면 검색페이지로 갈수있도록 수정해보자. tipuesearch부분에 가서 아이콘을 찾아서 `<a>`태그 안에 들어가도록 수정해주고 눌렀을때 검색페이지로 가도록 링크를 달아주자.   

**_includes > body > menu.html**   
```html
<!--검색 tipuesearch -->
<div class="nav-span">
    <form action="/search">
        <div class="tipue_search_left">
            <a href="/search/">
                <img src="/assets/tipuesearch/search.png" class="tipue_search_icon">
            </a>
        </div>
        <!--생략-->
```
![아이콘링크](/assets/img/blog/mobile5.png){: width="50%" height="50%"}   
아이콘을 눌러서 검색페이지로 오면 검색페이지의 검색창까지 사라져버린걸 알수있다!!!🤣 

### html selector 수정
**_includes > body > menu.html**   
검색페이지의 검색창과 탑메뉴바의 검색창에 서로 다른 css를 설정해주어야한다. 다시 tipuesearch부분에서 탑메뉴바의 검색창인 `<input>`태그의 `id`를 `tipue_search_input_menu`로 수정해주었다.

```html
<!--검색 tipuesearch -->
        <!--생략-->
        <div class="tipue_search_right">
            <input type="text" name="q" id="tipue_search_input_menu" pattern=".{1,}" title="At least 1 characters" required>
        </div>
        <div style="clear: both;"></div>
    </form>
</div>
```
> 검색페이지의 검색창은 search.html 에 있다!


원래있던 `#tipue_search_input`을 다시 살려서 검색페이지의 검색창에 적용시키고, `#tipue_search_input_menu`로 변경된 탑메뉴바의 검색창에도 없어지도록 적용해준다.

**assets > tipuesearch > css > tipuesearch-mobile.css**   
```css
/* search box */
#tipue_search_input{
     color: #333;
     max-width: 150px;
     max-height: 20px;
	padding: 15px;
	border: 2px solid #e3e3e3;
	border-radius: 0;
	-moz-appearance: none;
	-webkit-appearance: none;
     box-shadow: none; 
	outline: 0;
	margin: 0;
     /*text-align: center;*/
}

#tipue_search_input_menu{
     display: none;
}
```

검색페이지의 검색창은 생겼지만 이번엔 큰 화면일때 탑메뉴바의 css가 깨진다!🤣   
![검색페이지 검색창](/assets/img/blog/mobile6.png){: width="50%" height="50%"}   


### 바뀐 selector에도 css 적용
`#tipue_search_input_menu`에도 원래의 css를 적용시켜주면 된다.
`#tipue_search_input`에 적용중인 폰트에 `#tipue_search_input_menu`도 추가해주자. 

**assets > tipuesearch > css > tipuesearch.css**  (**tipuesearch-mobile.css**도 똑같이 폰트를 적용해주자.)
```css
/* fonts */
#tipue_search_input, #tipue_search_foot_boxes, #tipue_search_input_menu
{
     font: 300 14px/1 Roboto, sans-serif;
}
```

검색창 모양에도 `#tipue_search_input_menu`를 추가해주자.
```css
/* search box */
#tipue_search_input, #tipue_search_input_menu
{
     color: #333;
     max-width: 150px;
     max-height: 20px;
	padding: 15px;
	border: 2px solid #e3e3e3;
	border-radius: 0;
	-moz-appearance: none;
	-webkit-appearance: none;
     box-shadow: none; 
	outline: 0;
	margin: 0;
     /*text-align: center;*/
}
```

반응형 웹 완성!   
![웹 검색창](/assets/img/blog/mobile7.png){: width="70%" height="70%"}     
![모바일 검색창](/assets/img/blog/mobile2.png){: width="50%" height="50%"}     


<br>
<br>

- - -

## Reference 
- <http://www.tcpschool.com/html-tags/link>
- <https://jellybrown.tistory.com/40>
- <https://meaningone.tistory.com/115>