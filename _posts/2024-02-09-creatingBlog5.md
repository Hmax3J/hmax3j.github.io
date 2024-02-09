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
아니 또 설정이야 ? <a href='https://hmax3j.github.io/posts/creatingBlog4/' target='_blank' style='color:red'>Four포스팅</a>에서 한 거 아니야? 라고 할 수 있겠지만 아니였던 것이다.. <br>
필자는 로컬에서 화면 구성이 잘 되었길래 깃 데스크톱으로 레포지토리에 push를 해보았다. <br>
하지만 바아아아로 build 실패.. <br>
![gitCICD5](/assets/img/postImg/GitHubBlog/createBlog5/gitHubBuild5.JPG) <br>
위 이미지를 확인하려면 Actions에 들어가면 된다. <br>
build가 왜 실패 되었는지 몰라서 한참을 찾아 보았다.
<!-- 여기서는 설 끝나고와서 하기. 2024. 2. 9. -->