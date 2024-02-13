---
title: "깃허브 블로그 만들기 - Five"
date: 2024-02-09 02:45:00 PM +09:00
categories: [GitHubBlog]
---
***

>## <span style='color:#1E90FF'>깃허브 액션이란 ?</span>
<span style='background-color:LavenderBlush; color:red'>깃허브에서 제공하는 CI / CD 도구다.</span> <br>
레포지토리에서 발생하는 이벤트에 설정을 하여 워크플로우를 구성할 수 있다. <br>
깃허브 블로그를 만들 때에는 Deep하게 들어가면 힘들 것 같아서 <br>
자세한 것은 추후에 다른 카테고리에 포스팅 할 예정이다. <br>
이제 깃액션으로 빌드 및 배포를 해보자. <br>

>## <span style='color:#1E90FF'>페이지서비스 구성</span>
깃허브 레포지토리에 블로그로 사용할 레포지토리로 이동한다. <br>
![gitCICD1](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild1.JPG) <br>
이동했다면 위 이미지와 같이 1, 2, 3 순으로 클릭한다. <br>
![gitCICD2](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild2.JPG) <br>
Source를 클릭하면 위 이미지와 같이 나타나는데 Github Actions를 클릭하자. <br>

>## <span style='color:#1E90FF'>빌드와 배포를 해보자.</span>
페이지 서비스 구성이 끝났으면 이제 빌드와 배포를 할 시간이다. <br>
레포지토리에서 Actions를 클릭해보자.
![gitCICD3](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild3.JPG) <br>
위 이미지와 같은 페이지로 이동하게 될 것이다. 페이지 구성 후 액션으로 넘어오면 초기에는 <br>
![gitCICD4](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild4.JPG) <br>
워크플로우 부분이 이와 같이 나올 것이다. 이렇게 안나올 수도 있따.. 기억이 나질 않는다... <br>
필자는 이미 빌드와 배포를 해서 초기화면이 없어졌다. <br>
빌드와 배포를 하게 된다면 워크플로우에 변화가 생길 것이다. <br>
빌드와 배포는 chirpy 테마 제작자가 이미 깃허브 액션 파일을 만들어 놓았다. <br>
그것이 바로 .github/workflows/에 있는 pages-deploy.yml 파일이다. <br>
이제 이 파일을 본인의 환경에 맞게 바꾸어 주면 된다. <br>

>## <span style='color:#1E90FF'>pages-deploy.yml 환경설정을 해보자.</span>
아니 또 설정이야 ? <a href='https://Hmax3J.github.io/posts/creatingBlog4/' target='_blank' style='color:red'>Four포스팅</a>에서 한 거 아니야? 라고 할 수 있겠지만 아니였던 것이다.. <br>
필자는 로컬에서 화면 구성이 잘 되었길래 깃 데스크톱으로 레포지토리에 push를 해보았다. <br>
하지만 바아아아로 build 실패.. <br>
![gitCICD5](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild5.JPG) <br>
위 이미지를 확인하려면 Actions에 들어가면 된다. <br>
build가 왜 실패 되었는지 찾아 보았다.
![gitCICD6](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild6.JPG) <br>
위 이미지와 같이 에러가 나왔는데 노드 16을 지원을 안하니 노드 20으로 올려라 라는 얘기를 한다. <br>
현재 설정된 yml에는 노드 관련 코드가 없는데 waring이 뜨니 당황스러웠다. <br>
이 부분에 대해서 계속 찾아봤지만 노드 버전 얘기는 setup node를 활용해야 하는데 여기선 쓰지 않는다. <br>
의문이었다. 그래서 일단 넘어가고 build 에러난 부분을 찾아보았다. <br>
![gitCICD7](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild7.JPG) <br>
Test Site 부분이 계속 에러가 났다. 경로가 잘못 설정되어 있다고 한다. <br>
하지만 로컬에서는 이미지가 제대로 잘 나왔다. 그래서 Test 부분에 주석을 걸었다. <br>
![gitCICD8](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild8.JPG) <br>
이렇게 주석을 걸고 다시 빌드를 했다. 하지만 역시 실패... <br>
![gitCICD9](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild9.JPG) <br>
자꾸 에러가 나니 정말 답답했다. 사람들이 안하는 이유가 있구나 싶기도 하고, <br>
플랫폼을 바꿔야 하나 생각이 간절하게 들었다. 하지만 여기까지 했는데 포기하고 싶지 않았다. <br>
엄청난 시간을 투자한 끝에 결국 무엇이 범인인지 찾아내었다. <br>
내가 사용하고 있는 루비 버전이 3.2.3 인데 아래 이미지 처럼 지원하는 루비 버전이 달랐다. <br>
![gitCICD10](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild10.JPG) <br>
루비 버전에 현재 쓰고 있는 루비 버전을 써야 한다고 해서 썼는데.... <br>
내가 사용하는 3.2.3이 없었다.. 그래서 결국 처음 설정 되어있던 3.2로 바꾸었다. <br>
![gitCICD11](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild11.JPG) <br>
이럴줄 알았으면 일단 3.2로 설정한 후 수정을 할 걸 그랬다. <br>
결국 빌드 성공 !! 그리고 홈페이지에 들어가보았다. 그런데 ..? <br>
이번엔 또 포스트가 올라오질 않았다... 휴 정말 지쳤다.. <br>
갱신 시간이 있다고 해서 20분 정도 기다렸는데도 포스트가 갱신이 안되었다. <br>
그래서 최후의 수단인 컴퓨터를 껏다키고 확인했는데 최후의 수단 마저 실패...!! <br>
이걸 어쩌지 하다가 정말 최최후의 수단인 내일 확인하기로 했다. <br>
하지만 다음날 확인했지만 그래도 갱신이 안되어 있었다. <br>
Ctrl + Shift + R을 누르면 분명 글이 보이는데 F5를 누르면 글이 보이지 않으니 정말 답답했다. <br>
그래도 결국 하나하나씩 푸쉬하면서 확인하니 무엇이 문제인지 알아냈다 !!!! 이 때 정말 소리 질렀다. <br>
보니까 js파일들이 gitignore에 설정되어 올라가지 않는 상태였다. 이걸 없애고 js파일을 같이 push했다. <br>
그랬더니 결국 갱신이 되었다. 진짜 진짜 힘들었다.... 하지만 결국 해냈다 !!! 성취감이 엄청났다. <br>
그래서 이렇게 글도 쓰고 있다. ㅎㅎ 포기하고 싶고 힘들었지만 결국 해내니까 기분이 너무 좋다. <br>
다음 포스팅도 얼른 쓰고 싶다 !

>## <span style='color:#1E90FF'>NEXT STEP. </span>
<blockquote class='prompt-tip'>다음 미션은 블로그 사이드바 수정을 해보자.</blockquote>
