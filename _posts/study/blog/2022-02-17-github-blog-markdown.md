---
layout: post
title: "post 작성을 위한 Markdown 기초"
tags: gitblog post markdown
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: post 작성을 위한 Markdown
categories:
    - study
    - blog
related_posts:    
    -    
---
# [Blog] post 작성을 위한 Markdown 기초
* 
{:toc}

## 마크다운이란?

Markdown은 텍스트 기반의 마크업언어로 2004년 존그루버에 의해 만들어졌으며 쉽게 쓰고 읽을 수 있으며 HTML로 변환이 가능하다. 특수기호와 문자를 이용한 매우 간단한 구조의 문법을 사용하여 웹에서도 보다 빠르게 컨텐츠를 작성하고 보다 직관적으로 인식할 수 있다. 마크다운이 최근 각광받기 시작한 이유는 [깃헙](https://github.com) 덕분이다. 깃헙의 저장소Repository에 관한 정보를 기록하는 README.md는 깃헙을 사용하는 사람이라면 누구나 가장 먼저 접하게 되는 마크다운 문서였다. 마크다운을 통해서 설치방법, 소스코드 설명, 이슈 등을 간단하게 기록하고 가독성을 높일 수 있다는 강점이 부각되면서 점점 여러 곳으로 퍼져가게 된다.

## 마크다운의 장단점

### 장점
~~~
1. 간결하다.
2. 별도의 도구없이 작성이 가능하다.
3. 다양한 형태로 변환이 가능하다.
4. 텍스트로 저장되기 때문에 용량이 적어 보관이 용이하다.
5. 텍스트파일이기 때문에 버전관리시스템을 이용하여 변경이력을 관리할 수 있다.
6. 지원하는 프로그램과 플랫폼이 다양하다.
~~~

### 단점

~~~
1. 표준이 없다.
2. 표준이 없기 때문에 도구에 따라 변환방식이나 생성물이 다르다.
3. 모든 HTML 마크업을 대신하지 못한다.
~~~

## 마크다운 문법   

### 1. 헤더   

```
# this is a h1
## this is a h2 
### this is a h3 
#### this is a h4 
##### this is a h5 
###### this is a h6
```

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
# this is a h1
## this is a h2 
### this is a h3 
#### this is a h4 
##### this is a h5 
###### this is a h6
</div>
</details>

### 2. 코드블럭   
박스를 4가지 방식을 사용하여 나타내본다.

1. ```<pre><code>```
2. <code>```</code> 또는 <code>~~~</code>
3. 들여쓰기
4. 언어별 코드블럭 

**2.1 ```<pre><code>``` 사용**   

~~~
<pre>
<code>
def func(a,b):
    return a+b

print(func(2,3))
</code>
</pre>
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
<pre>
<code>
def func(a,b):
    return a+b

print(func(2,3))
</code>
</pre>
</div>
</details>  

<br>

**2.3 들여쓰기 사용**   
탭이나 스페이스 4번을 통해 코드블럭을 만들수 있다.

~~~
    def func(a,b):
        return a+b

    print(func(2,3))
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
    def func(a,b):
        return a+b

    print(func(2,3))
</div>
</details>  

<br>

**2.4 언어별 코드블럭 사용**   
python
<pre>
<code>
~~~python
def func(a,b):
    return a+b

print(func(a,b))
~~~
</code>
</pre>

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
~~~python
def func(a,b):
    return a+b

print(func(a,b))
~~~
</div>
</details> 

<br>
<details>
<summary>그밖에 언어들</summary>
<div markdown="1">
- Bash (bash)
- C# (cs)
- CSS (css)
- Diff (diff)
- HTML, XML (html)
- Ini (ini)
- JSON (json)
- Java (java)
- JavaScript (javascript)
- PHP (php)
- Perl (perl)
- Python (python)
- Ruby (ruby)
- SQL (sql)
</div>
</details>

### 3. BlockQuote (인용문)

~~~
> This is a first blockquote
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
> This is a first blockquote
</div>
</details> 

<br>
~~~
>> This is a second blockquote
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
>> This is a second blockquote
</div>
</details> 

<br>
~~~
>>> This is a third blockquote
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
>>> This is a third blockquote
</div>
</details> 

<br>

**blockquote 안에 다른 마크다운 요소를 포함할 수 있다.**

~~~
> * list1
> * list2
>   ~~~
>   code
>   ~~~
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
> * list1
> * list2
>   ~~~
>   code
>   ~~~
</div>
</details> 


### 4. 글머리 기호

~~~
+ 글머리
  + 글머리2
    + 글머리3
      + 글머리 4
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
+ 글머리
  + 글머리2
    + 글머리3
      + 글머리 4
</div>
</details> 



### 5. 강조 

~~~
*single asterisks*  
_single underscores_  
**double asterisks**  
__double underscores__  
~~cancelline~~  
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
*single asterisks*  
_single underscores_  
**double asterisks**  
__double underscores__  
~~cancelline~~  
</div>
</details> 

### 6. 기호표시

Markdown에서 이미 사용되는 기호 표기하기

Markdown 문법에 사용되는 기호를 있는 그대로 표시하고 싶을 경우가 있다.  
예를 들어 \#을 기호 그대로 사용하고 싶지만 그냥 쓰면 H1 헤더로 출력된다.  
그런 기호들을 아래에 표기하였다.

~~~
\   backslash
*   asterisk
_   underscore
{}  curly braces
[]  square brackets
()  parentheses
#   hash mark
+   plus sign
-   minus sign (hyphen)
.   dot
!   exclamation mark
~~~

이런것들을 사용하고 싶다면 기호앞에 \\(=back slash)를 붙혀주면 된다.  

### 7. 수평

~~~
* * *

***

*****

----

- - -
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
* * *

***

*****

----

- - -
</div>
</details> 

### 8. 링크 

- 외부 링크   
\[링크 키워드\]\(링크 주소\)
~~~
예 : [내 블로그](https://dev-dahye.github.io/about)
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
[내 블로그](https://dev-dahye.github.io/about)
</div>
</details> 

<br>
- 자동 링크  

~~~
예 : <https://dev-dahye.github.io/about>
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
<https://dev-dahye.github.io/about> 
</div>
</details>   

### 9. 이미지 

이미지 크기 조절은 뒤에 {: width='50%' height='50%'}

~~~
![그림1](/assets/img/myBlog/img9.jpg)
![그림2](/assets/img/myBlog/img9.jpg){: width='50%' height='50%'}
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
![그림1](/assets/img/myBlog/img9.jpg)
![그림2](/assets/img/myBlog/img9.jpg){: width='50%' height='50%'}
</div>
</details>  

### 10. 줄바꿈

마크다운에서는 엔터를 한번친다고 줄바꿈이 일어나지 않는다.  

**10.1 ```<br>``` 사용**

~~~
줄 바꿈시 사용 <br>
줄 바꿈시 사용
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
줄 바꿈시 사용 <br>
줄 바꿈시 사용
</div>
</details>    

<br>

**10.2 Enter 2번**

~~~
줄 바꿈시 사용  


줄 바꿈시 사용
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
줄 바꿈시 사용  


줄 바꿈시 사용
</div>
</details>  

<br>

**10.3 스페이스바 2번**

~~~
줄 바꿈시 사용    
줄 바꿈시 사용
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
줄 바꿈시 사용    
줄 바꿈시 사용
</div>
</details>  

### 11. 표

~~~
| ------ | NumPy | PyTorch |
| ------ | -------- | ---------- |
| 선언 | np.array() | torch.FloatTensor, <br/> torch.Tensor()|
| 차원 확인 | .ndim | .dim()|
| 크기 확인 | .shape | .size()|
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">

| ------ | NumPy | PyTorch |
| ------ | -------- | ---------- |
| 선언 | np.array() | torch.FloatTensor, <br/> torch.Tensor()|
| 차원 확인 | .ndim | .dim()|
| 크기 확인 | .shape | .size()|

</div>
</details>  

### 12. Expander control 

마크다운에서 접기/펼치기 가능한 컨트롤 문법  
마크다운 자체에는 기능이 없고 html을 이용 --> html의 details 사용

~~~html
<details>
<summary>접기/펼치기 버튼</summary>
<div markdown="1">

|제목|내용|
|--|--|
|1|1|
|2|10|

</div>
</details>
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">

<details>
<summary>접기/펼치기 버튼</summary>
<div markdown="1">

|제목|내용|
|--|--|
|1|1|
|2|10|

</div>
</details>

</div>
</details>  

<br>

~~~html
<details>
<blockquote>
    숨김숨김
</blockquote>
</details>
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">

<details>
<blockquote>
    숨김숨김
</blockquote>
</details>

</div>
</details>  


### 13. 이모지 

1. 'Window 키' + ';' 또는 'Window 키' + '.'

2. <http://www.iemoji.com/> 📝✏️✒️💡 🧰 🙋🏻‍♂️


### 14. 수학수식

[수학 수식 참고1](https://jjycjnmath.tistory.com/117)   
[수학 수식 참고2](https://ko.wikipedia.org/wiki/%EC%9C%84%ED%82%A4%EB%B0%B1%EA%B3%BC:TeX_%EB%AC%B8%EB%B2%95)   

~~~
$$x + y = 1$$
~~~

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
$$x + y = 1$$
</div>
</details>  

<br>

## html태그 커스텀&만들기

`_sass > my-style.scss` 에 추가   

```css
.markdown-body > p > a{
  font-weight: bold !important;
}

.markdown-body{
  kbd {
    font-size: 15px;
    font-family: monospace;
    color: #555;
    background-color: #fcfcfc;
    border: solid 1px #ccc;
    border-radius: 3px;
    border-bottom-color: #bbb;
    padding: 3px 5px;
  }

  mark {
    padding: 3px 5px;
    background-color: #fff9c4;
  }

  under {
    text-decoration: underline;
    text-decoration-color: red;
    text-underline-position: under;
    padding-bottom: 2px;
  }
}
```

```
<kbd>hello</kbd>

<a>hello</a>

<code>hello</code>

<mark>hello</mark>

<under>hello</under>
```

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
<kbd>hello</kbd>

<a>hello</a>

<code>hello</code>

<mark>hello</mark>

<under>hello</under>
</div>
</details> 

<br>

```css
.markdown-body{
  success {
    margin: 2em 0 !important;
    padding: 1em;
    display: block;
    color: #222831;
    font-size: .75rem !important;
    text-indent: initial;
    background-color: #CFEDC9;
    border-radius: 0.3rem;
    padding: 3px 5px;
  }

  warning {
    margin: 2em 0 !important;
    padding: 1em;
    display: block;
    color: #222831;
    font-size: .75rem !important;
    text-indent: initial;
    background-color: #FFF9BD;
    border-radius: 0.3rem;
    padding: 3px 5px;
  }

  danger {
    margin: 2em 0 !important;
    padding: 1em;
    display: block;
    color: #222831;
    font-size: .75rem !important;
    text-indent: initial;
    background-color: #F3C1BF;
    border-radius: 0.3rem;
    padding: 3px 5px;
  }

  info {
    margin: 2em 0 !important;
    padding: 1em;
    display: block;
    color: #222831;
    font-size: .75rem !important;
    text-indent: initial;
    background-color: #AAE0DB;
    border-radius: 0.3rem;
    padding: 3px 5px;
  }
}
```
```
<success>notice를 위한 블럭<br>예시입니다.</success>
<warning>notice를 위한 블럭</warning>
<danger>notice를 위한 블럭</danger>
<info>notice를 위한 블럭</info>
```

<details>
<summary><b>🔍결과</b></summary>
<div markdown="1">
<success>notice를 위한 블럭<br>예시입니다.</success>
<warning>notice를 위한 블럭</warning>
<danger>notice를 위한 블럭</danger>
<info>notice를 위한 블럭</info>
</div>
</details> 

<br>
<br>

- - -

## Refernce 
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)