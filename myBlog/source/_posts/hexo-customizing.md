---
title: "Hexo 테마 커스터마이징"
date: 2018-04-10 09:18:12
categories: hexo
tags: ["hexo", "hexo theme", "hexo customizing"]
cover: /img/post/20180410-bg.svg
---

# Hexo 테마를 커스터마이징하다.
그렇다. 내 맘에 들지 않았다. 이 테마 저 테마 깔아봐도 몇프로 부족했다.
내 맘대로 해보고싶었지만 generate하면 public에 수정했던 css들이 날라가버려 적용이 안되더라.
답답한 맘에 hexo theme를 구조를 뜯어보고 고치기로 했다.
이 또한 웹개발자에겐 넘나리 쉽고 간편한 일일진 모르지만, 내 나름 힘든 과정이었음으로
누군가에게 도움이 되고자 포스팅 해보려한다.

<br>

## 1. hexo의 clean-blog테마를 먼저 깔아보자.
hexo를 깔면 기본으로 landscape라는 테마가 깔려있다.

<img src="/img/post/20180410-1.jpg" alt="landscape theme 화면 뷰">

음~ 너무나 맘에 들지 않는다. 나름 반응형까지 지원하는 테마지만 우리가 원하는
깔끔하고 시원한 테마는 아닌것 같다. 그래서 커스터마이징하기 수월하게끔 깨끗한 clean-blog를 일단 깔아보았다.

방법은 너무나도 친절하게 정리해주신 아래 블로거님의 스텝을 따라하도록한다.

> <a href="https://kdydesign.github.io/2017/07/07/hexo-themes/">Hexo와 Github page로 만든 블로그에 Hexo 테마 적용하기 -Dev DY님</a>

<img src="/img/post/20180410-2.jpg" alt="clean-blog 테마 화면 뷰">

위와 같은 모습으로 설치된다.
그치만 나는 사이드메뉴도 넣고 싶었고 추후 프로필 페이지도 따로 멋있게 만들고 싶었다.
그러기 위해선 hexo의 구조부터 알아야 했다.

<br>

## 2. hexo 구조를 파악하자.

<img src="/img/post/20180410-3.jpg" alt="헥소 구조">

일단 hexo를 설치한 깃허브페이지의 최상단의 폴더를 보면 위와 같다. 여기서 눈여겨 봐야할 폴더와 파일은.. 

1. public : 이 폴더는 다른 폴더안에 있는 theme와 source 및 congif파일들이 generate 된 뒤 생성되는 정적파일들이 모이는 곳이다.
2. source : 우리가 작성할 post가 들어가는 폴더이다. post안에 작성한 tags, categorise 등이 source안에 구분되어 데이터로 쌓인다.
3. theme : 내가 다운로드한 테마가 담겨있는 폴더이다. 기본테마인 landscape와 clean-blog가 담겨 있을 것이다.
4. ＿config.yml : github page의 초기 설정값들이 담겨있다. 여기에 작성한 것들을 함수화해서 generate시 각 파일에 흩뿌려 public을 생성한다.

> 제가 이해한대로 작성했습니다. 틀린 것이나 오류가 있다면 댓글부탁드립니다.

public은 아무리 수정해대도 결국 generate하면 다 날라가 버린다. 
그렇다면 theme안의 어떤 것들이 정적파일로 생성되어 public에 들어간단 의민데
그럼 theme는 어떤 구조를 띄고 있는지 살펴봐보자.

<img src="/img/post/20180410-4.jpg" alt="헥소 테마 구조">

> languages는 config에서 언어를 뭘로 설정하느냐에따라 보여질 문구가 들어있는 것 같다. 한글은 없으므로 config의 언어설정은 그냥 en하면 된다. README에는 이 테마의 config를 작성하는 방법 및 포스트시 추가 가능한 내용들이 나와있다.

1. layout : 홈페이지의 각 부분을 따로따로 떼어논 .ejs(html형식) 파일들이 있다.
2. source : css와 img가 있는데, css는 stylus라는 프리프로세서를 통해 작성해놨다. 이또한 해당 부분에 따라 나눠져있다. img는 해당 (배경)이미지들이 존재한다.
3. ＿config.yml : 아까 상위에 있던 config와는 또 다른 config파일이다. 테마 안의 좀더 상세한 초기설정들을 할 수 있다. (작성법은 README를 참고.)

<br>

## 3. 커스터마이징에 필요한 환경을 구성하자.

위와 같은 구조이라고 했을 때, 나(혹은 퍼블리셔)의 기본 작업방식으로 작업하려면 먼저 html을 작성하고 css를 입히는 것 처럼 layout을 먼저 손봐야 한다.
(이 작업의 사전 지식이 되는 '웹의 기본 구조 및 형식'은 추후 포스팅 한 뒤 링크를 달아 놓겠다.)
나는 메뉴바 부분을 제일 먼저 수정하고 싶었으므로 menu가 들어있는 html의 조각을 찾아갔다.
찾는 방법은 아래와 같다.
먼저 html의 head와 body를 비롯한 모든 껍데기를 감싸고 있는 'myBlog/themes/clean-blog/layout/layout.ejs'를 연다.

``` html layout.ejs
<!DOCTYPE html>
<html <% if(config.language) { %>lang="<%= config.language %>"<% } else { %>lang="en"<% }%>>

<!-- Head tag -->
<%- partial('_partial/head') %>

<body>

    <!-- Menu -->
    <%- partial('_partial/menu') %>

    <!-- Main Content -->
    <%- body %>

    <!-- Footer -->
    <%- partial('_partial/footer') %>

    <!-- After footer scripts -->
    <%- partial('_partial/after-footer') %>

</body>

</html>
```

> 웹의 구조를 간단히 설명하자면 html(현재 표준은 html5)이라는 법칙안에 머리(head)와 몸(body)으로 구성 되어있다. 머리(head) 안에는 그 정신/생각이라 할 수 있는 meta tag들이 담겨있고 이것들은 눈(web 화면상)에 보이지는 않으나 이 웹페이지를 정의하고, 선언하는 역할을 한다. 
몸은 눈에 보여지는 부분이고 여기에 입력하는 모든 것은 웹 화면상에 나타난다. css란 이 몸에 옷을 입히는 일을 말하고 javascript/j-query등은 옷을 입힌 몸에 동력을 불어 넣는 일을 한다.

보다시피 전체 html구조가 나온다. 해당하는 부분이 각 ejs파일들로 인클루드 처리되어 있는 것 같다.
내가 고치려고 하는 menu의 경로도 확인 가능하다.
'myBlog/themes/clean-blog/layout/＿partial/menu.ejs'를 열어보자.

<img src="/img/post/20180410-5.jpg" alt="menu">

``` html menu.ejs_원본
<!-- Navigation -->
<nav class="navbar navbar-default navbar-custom navbar-fixed-top">
	<div class="container-fluid">
		<!-- Brand and toggle get grouped for better mobile display -->
		<div class="navbar-header page-scroll">
			<button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
				<span class="sr-only">Toggle navigation</span>
				<span class="icon-bar"></span>
				<span class="icon-bar"></span>
				<span class="icon-bar"></span>
			</button>
			<a class="navbar-brand" href="<%- config.root %>"><%- theme.menu_title || config.title || "" %></a>
		</div>
		<!-- Collect the nav links, forms, and other content for toggling -->
		<div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
			<ul class="nav navbar-nav navbar-right">
				<% for (var i in theme.menu){ %>
					<li>
						<a href="<%- theme.menu[i].url ? url_for(theme.menu[i].url) : url_for(theme.menu[i]) %>">
							<% if (theme.menu[i].icon) { %>
								<i class="fa fa-<%= theme.menu[i].icon %> fa-stack-2x"></i>
							<% } else { %>
								<%= i %>
							<% } %>
						</a>
					</li>
				<% } %>
			</ul>
		</div>
		<!-- /.navbar-collapse -->
	</div>
	<!-- /.container -->
</nav>
```

위와 같은 코딩을 볼 수 있다.
<% %> 에 해당하는 내용은 EJS* 언어임으로 건드리지 않는게 좋다. 
><a href="http://www.embeddedjs.com/">EJS</a> : EJS는 원래 JavaScriptMVC의 일부였던 클라이언트 측 템플릿 언어이며 현재 DoneJS로 대체되었다고 한다. 

일부 코딩을 바꿔 아래와 같이 수정해봤다.
``` html menu.ejs_수정
<!-- Navigation -->
<div class="custom-nav">
	<div class="menu-icon">
		<button>
			<span class="bar"></span>
			<span class="bar"></span>
			<span class="bar"></span>			
		</button>
	</div>
	<a class="logo" href="<%- config.root %>"><%- theme.menu_title || config.title || "" %></a>

</div>	

<div class="left-side" id="bs-example-navbar-collapse-1">
	<button class="close">
		<span class="bar"></span>
		<span class="bar"></span>
	</button>
	<div class="intro">
		<img src="/img/profile.jpg" alt="내사진">
		<p><a href="mailto:bomee88@naver.com"><strong>@봉치</strong></a>Front-end개발, 웹기획, 웹디자인까지 호기심많은 UI개발자입니다.</p>
	</div>
	<ul>
		<% for (var i in theme.menu){ %>
			<li>
				<a href="<%- theme.menu[i].url ? url_for(theme.menu[i].url) : url_for(theme.menu[i]) %>">
					<% if (theme.menu[i].icon) { %>
						<i class="fa fa-<%= theme.menu[i].icon %> fa-stack-2x"></i>
					<% } else { %>
						<%= i %>
					<% } %>
				</a>
			</li>
		<% } %>
	</ul>
</div>
```

기존의 navbar, navbar-default, navbar-custom, navbar-fixed-top 등의 클래스명은 부트스트랩의 일환이므로 css 중복을 방지하기 위해 과감히 삭제하고
새로운 클래스명 'custom-nav'를 사용해 내가 원하는 css와 js를 입힐 것이다.
그럼 이제 css와 js를 커스터마이징해보자.

'myblog/public'으로 들어가보면 css와 js폴더가 존재한다.

<img src="/img/post/20180417-1.jpg" alt="">

거기에 각각의 customizing.css, customizing.js를 만들어 넣자.

<img src="/img/post/20180417-2.jpg" alt="">
<img src="/img/post/20180417-3.jpg" alt="">

이제 우리가 만든 customizing파일들을 html에 링크를 연결해야한다.
아까 껍데기 부분이었던 'myBlog/themes/clean-blog/layout/layout.ejs'를 다시 확인해보자.

``` html layout.ejs
<!DOCTYPE html>
<html <% if(config.language) { %>lang="<%= config.language %>"<% } else { %>lang="en"<% }%>>

<!-- Head tag -->
<%- partial('_partial/head') %>

<body>

    <!-- Menu -->
    <%- partial('_partial/menu') %>

    <!-- Main Content -->
    <%- body %>

    <!-- Footer -->
    <%- partial('_partial/footer') %>

    <!-- After footer scripts -->
    <%- partial('_partial/after-footer') %>

</body>

</html>
```

css는 html의 head부분에 존재한다.
그렇다면 partial의 Head tag라고 표기된 부분의 '＿partial/head.ejs'파일을 열면 되겠다.

<img src="/img/post/20180417-4.jpg" alt="">

다른 메타태그부분들이 즐비하지만 우리가 눈여겨 봐야 할 곳은 빨간 사각형인 custom css부분이다. 
위의 사진과 같이 customizing.css 를 link해준다.

그 다음은 js다. js는 보통 head에 위치하기도 하지만, html이 모두 로드된 뒤에 자연스럽게 js가 돌아가도록 하기위해 body제일 아랫부분에 위치하기도 한다. head에 js가 없었으니 body의 아랫부분인 after-footer.ejs를 확인해보자.

<img src="/img/post/20180417-5.jpg" alt="">

역시나 존재하는구나! 
우리의 customizing.js를 삽입해주고 저장하고 닫는다.

이제 드디어 커스터마이징 할 수 있는 모든 환경을 만들어 놓았다.
위의 예시는 menu뿐이었지만 그 외에 여러분이 원하는 어떤 영역이든 layout에서 확인 한 뒤 
html(.ejs)를 고치고 customizing.css에서 css를 입히고 customizing.js에서 동작을 만들어주면 된다.
css와 js를 다룰 줄 아는 사람이라면 누구든지 hexo를 커스터마이징 할 수 있을 것이다.


여기까지로 hexo customizing 포스팅은 마치고..
다음 포스팅 부터는 필자의 주된 영역인 웹표준, 반응형 웹, html, css, j-query 등에 대해서 다뤄보도록 하겠다.
