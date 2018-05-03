---
title: "아무나 깃허브 페이지 만들기"
date: 2018-04-05 13:33:05
tags: ["github","github_page","git"]
categories: github
---

# 깃허브페이지를 만들다.
깃허브페이지로 블로그 만들기가 정말 쉽지않았다. 
커맨드라인이 생소해서 깃허브 데스트탑을 다운받아 이용해봤는데 구글링 자료들이 많지 않아 결국엔 깃을 설치하게 됐다. Git, Node.js, hexo까지.. 쉽지않았지만 기나긴 구글링 끝에 성공했다. hexo 테마가 마음에 들지않아 커스터마이징하기 위해 또 hexo구조까지 뜯어가며 공부한 결과 그나마 지금의 구색을 갖추게 되었다.

부랴부랴 만들고나니 웹에 대한 지식이 전무한 사람도 이해할 수 있을만한 포스팅이 있었으면 좋겠다고 생각했다.

좀 어설프긴 하지만 그래도 내가 밟아간 과정을 남겨보려한다.

-------------

<br>
## 필수요소 설치

아래는 깃허브페이지를 만들기 위해 필요한 것들을 우리가 알아야할 부분만 요약해봤다.
 1. <a href="https://git-scm.com/">git</a> : 간단히 말해 버전관리앱이라고 한다. 더 많은 설명은 구글링을 대신하고 우리는 여기서 git bash를 통해 까만창에 명령어들을 써댈것이다.
 2. <a href="https://github.com/">git hub</a> : 깃허브는 우리가 접속할 웹계정을 생성할 공간이다. 로컬에서 프로젝트를 작성하고 나의 깃허브웹에 업로드해 누구나 볼 수 있게 한다. 
 3. <a href="https://nodejs.org/ko/">node.js</a> : 자바스트립트 런타임이라고 한다. 간단히 큰 오픈 소스 라이브러리라고 보면 될 것 같다. 일단 노드도 설치해야한다. 이걸 통해 hexo라는 깃허브페이지 테마를 설치 할 것이다.
 4. <a href="https://hexo.io/ko/">hexo</a> : 빠르고 간단하고 강력한 블로그 프레임워크라고 사이트에 자기소개하고있다. 지킬기반의 블로그 테마라고 보면 될 것 같다.

<br>
## 1. 깃허브 가입 및 레포지토리 생성하기
<a href="https://github.com/">깃허브</a>에 가입한다.


<img src="/img/post/20180405-1.jpg" alt="깃허브 가입하기">
>빨간부분의 내용을 잘 입력하여 가입하면 된다. 메일주소는 나중에 인증해야 하기 때문에 유효한 것으로 적어야 한다.

<br>

<img src="/img/post/20180406-1.jpg" alt="레포지토리 생성하기">
>가입한 뒤에 빨간 표시 부분의 New repository를 클릭해서 새로운 레포지토리를 만든다.

<br>

<img src="/img/post/20180406-2.jpg" alt="레포지토리 생성하기2">
>위 그림과 같이 레포지토리 이름은 "사용자아이디".github.io 로 생성하고, 
공개여부는 Public으로 선택한 뒤 아래 초록버튼 Create repository 버튼을 누른다.

<br>
## 2. 깃 설치하기
<a href="https://git-scm.com/downloads">이 곳을 눌러 깃을 설치</a>한다.

<img src="/img/post/20180406-3.jpg" alt="깃 설치하기1">
>위 링크로 들어가 자신의 PC에 맞는 OS를 클릭하면 자동으로 다운로드 된다.

<br>

<img src="/img/post/20180406-4.jpg" alt="깃 설치하기2">
>다운로드 후 실행시켜 Next를 열심히 눌러 설치한다.

<br>

## 3. 로컬과 깃허브 연결하고 hexo설치하기

자 이제 내 PC와 깃허브 저장소를 연결해보자. 아까 열심히 설치한 git에서 git bash를 실행한다. 

<img src="/img/post/20180406-5.jpg" alt="깃바쉬 열기">
>탐색기에서 git bash를 검색해서 열면 된다.

그 뒤 아래와 같이 입력하면 된다.
이 작업은 

```
$ git config --global user.name "Your Name Here"
```
>"$"는 창에 달려있으므로 따로 안써줘도 되고 그 뒤부터 써내려가면 된다. your name에 내아이디를 넣는다.

<img src="/img/post/20180406-6.jpg" alt="깃바쉬 열기">

위와 같이 작성하면 된다. 근데 이게 잘 알아들은건지 뭔지 기분나쁘게 또 입력하라는 창만 나오고 반응이 없어? 싶을때는 아래와 같이 써볼수도 있다.

```
$ git config --global user.name
```

사실 아직도 git과 github를 완전히 이해하진 못하겠다.
넘나 생소하고 먼 그대들이기에 
그 이후의 과정은 아래 블로그로 대체한다.

><a href="https://nolboo.kim/blog/2013/10/06/github-for-beginner/">완전 초보자를 위한 깃허브</a>

헥소 설치과정은 아래 블로그로 대체한다.

><a href="https://www.holaxprogramming.com/2017/04/16/github-page-and-hexo/">Github Page와 Hexo를 통해 30분만에 기술 블로그 만들기</a>

위 블로그 외에도 
><a href="https://hexo.io/ko/docs/">hexo 소개 페이지</a>
만 읽어도 충분히 설치 가능하다. 왜냐면 한글판이기때문에^^..

hexo를 설치하고 로컬과 깃허브를 연결했다면 그 위치에서 깃바쉬를 바로 열 수 있다.
<img src="/img/post/20180409-1.jpg" alt="로컬에서 깃바쉬열기">

그런 뒤 아래와 같이 입력하면 로컬서버에서 바로 웹화면의 모습을 미리 볼 수있다.

```
$ hexo server
```

<a href="http://localhost:4000">http://localhost:4000</a>
브라우저에 위와 같이 입력해보자. 웹서버에 올렸을 모습을 바로 확인가능하다.
로컬에서 모든 수정작업을 마친 뒤 generate하여 정적파일들을 생성한다. 

```
$ hexo g
```
>가늠컨데 이 작업을 통해 각각 분산되어있던 config.yml, .md(마크다운), .ejs, .styl(스타일러스) 파일들이 public폴더 안에 정적 파일들로 생성되는 것 같다.

그리고 나서 로컬서버 주소로 다시 확인해본다.
더이상 변동할 내용이 없을 경우 웹사이트에 deploy한다.

```
$ hexo -d
```
> deploy후 서버에 반영되는 시간이 몇분 걸리긴 한다. 1~2분 지나도 적용이 안되거나 스타일이 깨져보이는 경우가 생기면 웹에 저장되어있는 기존 캐시때문임으로 브라우저 설정에서 캐시를 삭제하도록한다. (크롬브라우저 기준 단축키 'Ctrl+Shift+R')

<br>
## 4. 포스트 작성하기
포스트를 작성할때도 기본적인 html 상식정도는 알아야 가능하다.
h1, h2, h3, div, a태그 등 이런거 뭔지 하나도 모르겠다 하시는 분들은 네이버나 브런치 등 에디터 달려있는 블로그를 이용하심이 좋을 것 같다.

3번의 링크들을 통해 순서대로 설치하고 폴더 구조를 보면 아래와 같이 되어있다.

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

여기서 source에 posts 폴더로 들어가면 제일먼저 만나게 되는 것이 .md(마크다운)파일이다.
마크다운은 우리가 아는 기존의 마크업 방식보다 좀더 유연하고 편리하다. 
아래의 링크를 들어가면 작성하는 방법이 나와있다.
마크다운 파일이라고 마크다운만 작성법만 사용가능한가 했더니 기존의 마크업방식도 반영되고, hexo 안의 hexo-writing방법도 사용가능하더라. 

### 포스트 작성 문법
 1. html 기본문법(마크업)
 2. <a href="https://gist.github.com/ihoneymon/652be052a0727ad59601">마크다운</a>
 3. <a href="https://hexo.io/ko/docs/writing.html">Hexo Writing</a>(hexo설치 시)

html 기본문법은 우리가 흔히 보는 마크업이기때문에 생략하고,
마크다운과 hexo-writing사용법은 각 이름에 걸어둔 링크를 참조하도록 한다.
나는 세가지 방법중 마크업과 마크다운을 섞어서 사용하는 중이다. 
마크업보다 훨씬 편한거같다.

아! 나는 에디터로 <a href="https://www.sublimetext.com/3">Sublime Text 3</a>를 사용하고 있는터라 아래와 같은 모습으로 편리하게 편집이 가능한데.. 혹여 에디터 없이 편집하시는 분들이 계실지도 몰라 편집화면 모습을 공유해본다. (링크 눌러 다운로드 가능하다.)
<img src="/img/post/20180409-2.jpg" alt="서브라임텍스트 사용화면">
> Package Control의 Install Package를 사용해서 다운로드하면 각종 파일형식이 다 지원이 된다. 

서브라임만 4년째 이용중인데 '이렇게만 되면 편할텐데~' 라고 생각한 것들을 구글링 해보면 모든 패키지가 이미 다 나와있을 정도로 빠르고 편리하다. 자세한건 나중에 기회가 되면 포스팅하도록 하겠다.

다음에는 hexo테마를 좀더 분석해보고 어떻게 내가 원하는대로 커스터마이징 할 수 있는지 정리해서 올려보려한다. 
포스팅 정말 쉬운게 아니구나.
그럼 이만~
