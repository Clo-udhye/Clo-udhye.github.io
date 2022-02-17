---
layout: post
title: "블로그 시작하기"
tags: gitblog Jekyll
image: 
    path: /assets/img/blog/gitBlog.png
accent_color: '#01ADB5'
description: >
    깃허브 블로그 만들기: 블로그 시작하기
categories:
    - study
    - blog
related_posts:    
    -    
---
# [gitBlog] 블로그 시작하기
### Jekyll
Jekyll은 블로그 템플릿을 제공받아 약간의 커스텀만 하고 포스팅하는데 집중할 수 있게 해주는 블로그 생성기이다.
Jekyll 테마를 통해 블로그 테마를 다운로드하고 이미지와 색, 내비게이션 바 등을 수정하고 게시물을 업로드하고 Jekyll 을 통해서 컴파일을 하여 내가 운영할 수 있는 블로그 코드 파일, HTML, CSS, JS 파일을 얻는다.

*이 파일들을 자신의 레파지토리에 넣으면 블로그가 만들어진다.*

##### Jekyll의 특징
- Static website 를 만들어주는 도구
- Markdown → HTML 지원
- 수 많은 무료테마 존재
- GitHub Pages 가 추천하는 도구

### 지킬 무료, 유료 테마들을 다운 받을 수 있는 사이트

-  [http://jekyllthemes.org/](http://jekyllthemes.org/)
-  [https://jekyllthemes.io/free](https://jekyllthemes.io/free)
-  [https://jamstackthemes.dev/ssg/jekyll/](https://jamstackthemes.dev/ssg/jekyll/)
- [https://jekyll-themes.com/free/](https://jekyll-themes.com/free/)

> 직접 테마를 만들 수도 있다. 테마 작성 관련 튜토리얼은 다음 페이지를 참조하자.   
 [http://jekyllrb-ko.github.io/docs/step-by-step/01-setup/](http://jekyllrb-ko.github.io/docs/step-by-step/01-setup/)
 
마음에 드는 테마를 찾았다면, 해당 테마 페이지에 있는 다운로드 또는 github clone 으로 파일들을 다운 받자!

### Hydejack 테마로 시작하기
[http://themes.jekyllrc.org/hydejack/](http://themes.jekyllrc.org/hydejack/)에서 테마를 다운받고 원하는 위치에 압축을 풀자.
![Hidejack Theme설치](/assets/img/blog/setting1-1.png){:width="80%" height="80%"}
![Hidejack Theme설치](/assets/img/blog/setting1-2.png){:width="80%" height="80%"}
![Hidejack Theme설치](/assets/img/blog/setting1-3.png){:width="80%" height="50%"}

### Ruby와 Jekyll 설치하기
다운받은 파일을 수정하기 전에 Jekyll을 설치해야한다. 우리가 다운 받은 파일은 Jekyll기반으로 개발이 되어있기 때문에 Jekyll을 설치하지 않을 경우 우리가 원하는 방식으로 테마를 수정할 수가 없다.

Text로 우리가 작성한 Markdown, _config.yml등의 파일들은 Jekyll을 통해서 _site폴더내의 산출물로 변환되고 해당 산출물이 Github를 통해 WEB에서 실행되는 형태라고 할 수 있다.

jekyll 테마를 설치하고 수정, 관리하기 위해서는, 먼저 ruby 개발 환경을 세팅하고 주어야 한다.

- **Ruby 설치**
Jekyll이 Ruby로 만들어졌기 때문에 Ruby를 설치 해줘야한다. 윈도우 OS의 경우 Ruby와 개발툴킷을 별도로 설치해줘야 하므로 Ruby Install 페이지에 접속하여 아래와 같이 추천 다운로드 버전을 다운 받으면 된다.

다음 페이지에서 루비를 다운받고 설치 하자.   
[https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/)
![Ruby설치](/assets/img/blog/setting1.png){:width="70%" height="70%"}
> 어떤 버전으로 설치할지 고민된다면 Ruby가 추천해주는 것으로 설치하자.   

![Ruby설치](/assets/img/blog/setting2.png){:width="70%" height="70%"}    
별도 설정없이 Next만 누르면 잘 설치된다. 이때 체크박스는 모두 체크해준다.   

![Ruby설치](/assets/img/blog/setting3.png){:width="70%" height="70%"}   
1을 누르고 엔터한다. 쭉 설치가 되고 마지막에 엔터를 누르면 터미널이 꺼진다.   

cmd를 창을 열고 `ruby –v` 명령어를 입력하여 루비가 잘 설치되었는지 확인해 본다.   
![Ruby설치](/assets/img/blog/setting4.png){:width="70%" height="70%"}   

visual studio code로 다운받았던 테마 폴더를 열고 `ctrl+~`을 눌러 터미널을 연다.   
![Ruby설치](/assets/img/blog/setting5.png){:width="70%" height="70%"}   

chcp 65001를 실행한다. 인코딩을 부여하기 위한 명령어인데 실행하지 않을 경우 이후 진행하게 될 온갖 명령어에서 오류가 발생하므로 꼭 진행하여야 한다.

```bash
chcp 65001
```

이제 Ruby에서 지원하는 gem 명령어를 통해 Jekyll은 물론 종속된 필요한 라이브러리를 설치하자. 아래 코드와 그림을 참고하면 된다. 참고로, gem이란 루비에서 제공하는 라이브러리를 편리하게 설치할 수 있도록 지원되는 도구이다.

```bash
gem install bundler jekyll minima jekyll-feed tzinfo-data rdiscount
```

Bundler는 Jekyll 과 함께 사용하기에 탁월한 도구다. 프로젝트별로 의존요소들을 추적하기 때문에, 프로젝트에 따라 다른 버전의 Jekyll 을 사용해야 할때 특히 유용하다. Bundle을 install 하자.

```bash
C:\blog> bundle install
C:\blog> bundle update --bundler
\\ 가 안되신다면 -bunlder
C:\blog> bundle exec jekyll serve
```
아래와 같은 문구가 나오면   
![Bundler 설치](/assets/img/blog/setting6.png){:width="70%" height="70%"}   
컨트롤+C를 두번하여 종료하고   

`gem 'wdm', '>= 0.1.0'` 를 Gemfile의 가장 아래에 붙여주고 저장을 해준후 다시 `bundle exec Jekyll serve`입력하면 로컬에서 서버가 실행된다.

웹 브라우저에서 `localhost:4000`에 접속하면 블로그 완성!
![로컬서버](/assets/img/blog/setting7.png){:width="70%" height="70%"}   




Refernce
- [면접관이 좋아하는 Git Portfolio 만들기 (with_GitBlog)](https://projectlion.io/courses/technology/gitblog)