---
layout: post
title: "서브메뉴 펼쳐보기"
tags: gitblog submenu tooltip
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 서브메뉴 펼쳐보기, 툴팁
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] 서브메뉴 펼쳐보기
* 
{:toc}

## html 
**_includes/body/nav.html** 파일을 만들어 다음 코드를 삽입한다.
간단하게 코드를 설명하면 config.yml에 menu가 있다면 아래를 수행하는데 menu안에 요소들을 반복해서 list를 만든다. 그 리스트는 url이있어서 클릭하면 그 메뉴로 이동할 수 있다.   
submenu가 있다면 버튼을 생성하고 submenu 가 있으면 그 안에 subnode의 링크와 subnode의 타이틀을 리스트로 만든다.

```html
{% raw %}
<!--네비게이션바에 메뉴선정-->
<span class="sr-only">{{ site.data.strings.navigation | default:"Navigation" }}{{ site.data.strings.colon | default:":" }}</span>
<ul>
  {% if site.menu %}
    {% for node in site.menu %}
      {% assign url = node.url | default: node.href %}
      <!-- 메뉴 각각을 식별하기위한 인덱스 -->
      {% assign count = count | plus: 1 %}
      <li>
        <div class="menu-wrapper" onmouseover="javascript:spread({{count}})" onmouseout="javascript:spread({{count}})">
          <!-- submenu 변수는 _config.yml 에서 추가합니다 -->
          {% if node.submenu %}
            <!-- spread 함수는 js 파일로 작성하고 my-head.html에 추가합니다 -->
            <!-- spread-btn class는 my-style.scss에 추가합니다. -->
          <button class="spread-btn">
            <!-- marterial stylesheet를 my-head.html에 추가합니다 -->
              <span id="spread-icon-{{count}}" class="material-icons">arrow_right</span>
          </button>
          {% endif %}
          <a
            {% if forloop.first %}id="_drawer--opened"{% endif %}
            href="{% include_cached smart-url url=url %}"
            class="sidebar-nav-item {% if node.external  %}external{% endif %}"
            {% if node.rel %}rel="{{ node.rel }}"{% endif %}
            >
            {{ node.name | default:node.title }}
          </a>
        
          {% if node.submenu %}
          <div id="submenu-{{count}}" class="menu-wrapper submenu hide">
            <ul style="list-style: none;">
            {% for subnode in node.submenu %}
              <li>
                <a
                  class="sidebar-nav-item {% if node.external  %}external{% endif %}"
                  href="{% include_cached smart-url url=subnode.url %}"
                  >
                  {{ subnode.title }}
                </a>
              </li>
            {% endfor %}
            </ul>
          </div>
          {% endif %}
       </div>
      </li>
    {% endfor %}
  {% else %}
    {% assign pages = site.pages | where: "menu", true %}
    {% assign documents = site.documents | where: "menu", true %}
    {% assign nodes = pages | concat: documents | sort: "order" %}

    {% for node in nodes %}
      {% unless node.redirect_to %}
        <li>
          <a
            {% if forloop.first %}id="_navigation"{% endif %}
            href="{{ node.url | relative_url }}"
            class="sidebar-nav-item"
            {% if node.rel %}rel="{{ node.rel }}"{% endif %}
            >
            {{ node.title }}
          </a>
        </li>
      {% else %}
        <li>
          <a href="{{ node.redirect_to }}" class="sidebar-nav-item external">{{ node.title }}</a>
        </li>
      {% endunless %}
    {% endfor %}
  {% endif %}
</ul>
{% endraw %}
```

## javascript
**assets/js** 폴더를 만들고 sidebar-folder.js 파일을 만들어 다음 코드를 삽입한다.
```js
function spread(count){
    let submenu = document.getElementById('submenu-' + count);
    if(submenu){
        if(submenu.classList.contains('hide')) submenu.classList.remove('hide');
        else submenu.classList.add('hide');
    }

    let spreadIcon = document.getElementById('spread-icon-' + count);
    if(spreadIcon){
        if(spreadIcon.innerHTML == 'arrow_right') {
            spreadIcon.innerHTML = 'arrow_drop_down';
            spreadIcon.style.color = 'grey';
        }else{
            spreadIcon.innerHTML = 'arrow_right';
            spreadIcon.style.color = 'white';
        } 
    }
}
```

방금 추가한 js파일을 블로그에서 접근할수있게 **_includes > my-head.html** 맨위에 추가한다.

```html
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
<script src="/assets/js/sidebar-folder.js"></script>
```

## css
**_sass > my-style.scss** 에 다음 코드를 추가한다.

```scss
// 메뉴
.spread-btn{
  right: 15%;
  position: absolute;
  padding: 0;
  padding-top: 2px;
  border: none;
  background: none;
  color: white;
  cursor: pointer;
  z-index: 1;
}
.menu-wrapper {
  text-align: left;
  margin-left: 30%;
}
.submenu.menu-wrapper{
  right: 10%;
  position: absolute;
  background-color: rgb(142, 173, 194);
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.7);
  width: 10rem;
  z-index: 2;
  ul{
    margin: 0;
    padding: 0 1.25rem;
  }
}
.submenu.menu-wrapper.hide{
  display: none;
}
```

## 사이드바 툴팁 완성
![완성](/assets/img/blog/tooltip1.png){: width="70%" height="70%"}  

## 오류 수정
사이드바의 일정부분 밖으로 툴팁이 잘리는 오류를 발견했다.
![오류발견](/assets/img/blog/tooltip2.png){: width="70%" height="70%"}   

사이드바의 css를 가져와서 다음과 같이 수정했다.

```css
.sidebar-sticky{
  --hy-drawer-width: 100%;
  --hy-drawer-box-shadow: 0 0 1rem rgba(0, 0, 0, 0.25);
  --hy-drawer-peek-width: 21rem;
  cursor: grab;
  color: rgba(255,255,255,0.75);
  text-align: center;
  box-sizing: border-box;
  position: relative;
  z-index: auto;
  max-width: 21rem;
  padding: 1.5rem;
  contain: layout;
  opacity: 1;
}
```
`content:content` 를 `content:layout`으로 수정해줬는데, `contain` 속성은 특정 요소와 콘텐츠가 문서 트리의 다른 부위와 독립되어있음을 나타낼 때 사용한다.

> `contain: layout paint`와 같은데 `paint` 는 요소의 자손이 자신의 범위 바깥에 그려지지 않음을 나타냅니다. 이 값을 지정한 요소의 경우, 요소가 화면 밖에 위치할 경우 당연히 그 안의 자손도 화면 안에 들어오지 않을 것이므로 브라우저는 그 안의 요소를 고려하지 않아도 됩니다. 그러나 만약 자손이 범위 밖으로 넘칠 경우에는 요소의 테두리 상자에서 잘라냅니다.

![오류수정](/assets/img/blog/tooltip3.png){: width="70%" height="70%"}   


<br>
<br>

- - -

## Refernce 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)
-<https://developer.mozilla.org/ko/docs/Web/CSS/contain>