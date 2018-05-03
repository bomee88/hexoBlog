---
title: 깃허브로 다른컴퓨터에서 hexo블로그 수정하기
date: 2018-05-03 14:04:23
categories: github
tags: [github, hexo]
cover: /img/post/20180418-1.jpg
---

# 깃허브로 다른컴퓨터에서 hexo블로그 수정하고싶다!
그렇다 별것도 아닌데 이거 이해하는데 왜 이렇게 많은 시간이 걸렸는지 모르겠다.
이걸 자세히 설명해준 포스트도 정말 하나도 없었다!!!
나같이 두대의 컴퓨터에서 작업해야하는 사람을 위해서 지금까지의 방법을 포스팅 해보려한다.

---

## 첫번째 컴퓨터에서 해야할 사항
먼저 첫번째 컴퓨터에 폴더를 보자. 
hexo 블로그를 생성해주는 파일 전체를 담고있는 폴더가 있다.
예를 들면 나의 상황에서는 myblog폴더가 그러하다.

(사담주의)
myblog폴더 안에서 git bash를 실행하고 $hexo g -d (generate+deploy) 해서 깃허브에 바로 정적파일들을 생성하며 올려왔었더랬다. (모르신다면 <a href="https://bomee88.github.io/2018/04/05/first-post/">아무나 깃허브 페이지 만들기</a>를 참고)

이 당시...!
나는 myblog의 hexo deployer를 비롯한 모든 파일이 내 깃허브로 올라가는 줄 알았다.
그래서 레포지토리를 두개 만들어야된다는 설명을 지인에게 들었는데도 당췌 이해가 가지 않았더랬다. 
'왜 두개여야하지? 이미 내 파일들을 내 주소로 되어있는 레포지토리에 올리지 않았던가?' 하며 의아해했었다.
그런데 내 깃허브페이지를 잘 보니 public폴더 안의 내용만 올라가있지 않은가?

결국 $hexo generate로 public폴더안에 정적파일을 생성한것이고
$hexo deploy로는 그 정적파일들을 깃에 올리기 위해 '.deploy_git'폴더에 복사하고 이곳에 있는 것만 나의 깃허브페이지에 올리겠다는 의미로 사용하고 있었던 거다 ㅠㅠ
이걸 깨닫는데 5일이 소요되다니 ;ㅁ; 세상억울
(사담끝)

<img src="/img/post/20180503-1.jpg" alt="myblog 사진">
>myblog 폴더를 다시보자

<img src="/img/post/20180503-2.jpg" alt="public 사진">

<img src="/img/post/20180503-3.jpg" alt="깃허브 사진">
>myblog 전체가 아닌 myblog/public폴더만 깃허브에 올라가 있는 것을 확인할 수 있다.

정리하면, hexo로 블로그를 만들었을 경우 myblog안의 public에 해당하는 부분만 .deploy.git에 복사되어 깃허브페이지 레포지토리(https://github.io/username/username.github.io.git)에 올라간다.
그렇기때문에 다른 컴퓨터에서 같은 환경으로 작업하기 위해서는 hexo와 deployer를 모두 담고있는 myblog자체를 새로운 레포지토리로 생성해서 올려야 하는 것이다.
설명이 이해가 간다면 이제 새로운 레포지토리를 만들어보자.

(이 뒤는 집에가서 해봐야지)

git clone [주소입력]	//다운받고 싶은 곳을 클론하기
cd [주소파일]		//주소파일생성된 곳으로 들어가기
touch Readme.txt 	//시험용 리드미 파일 생성
git status		//새로 생성된 파일 상태 확인
git add Readme.txt 	//추가할 파일 깃에게 알리기
git commit -m "add Readme.txt"   //커밋작성하기
git remote add origin https://github.com/username/myproject.git //로컬과 원격 저장소를 연결 
git remote -v 		//연동상태 확인하기
git push origin master	//깃허브로 푸쉬하기