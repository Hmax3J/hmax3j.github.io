---
title: "깃허브 블로그 만들기 - Six"
date: 2024-02-12 06:00:00 PM +09:00
categories: [GitHubBlog]
tags: [githubblog, gitpage]
---
***

>## <span style='color:#1E90FF'>블로그를 꾸며보자.</span>
이제 본격적으로 블로그를 꾸며볼 시간이다. <br>
필자는 왼쪽 사이드바가 회색인게 너무 흔한 것 같고 예쁘지가 않아 바꾸고 싶었다. <br>
이제부터 왼쪽 사이드바를 수정해보자 ! <br>

>## <span style='color:#1E90FF'>사이드바 수정하기</span>
먼저 사이드바를 살펴보자. 아래 이미지와 같이 있을 것이다. <br>
![sideFix1](/assets/img/postImg/GitHubBlog/createBlog6/sideFix1.JPG) <br>
심플하지만 필자 마음에 들지 않았다. 그래서 바꿨다. <br>
타이틀부터 바꾸어 보자. 루트 디렉토리에 <span style='color:red'>_config.yml</span> 파일이 있을 것이다. 파일을 열어주자. <br>
![sideFix2](/assets/img/postImg/GitHubBlog/createBlog6/sideFix2.JPG) <br>
위와 같이 나올 것이다. lang과 timezone은 본인에 맞게 설정하면 된다. <br>
title은 블로그 이름이라 생각하면 된다. tagline은 부제목 <br>
description은 블로그 주소를 링크로 보낼 때 나오는 설명이라 보면 된다. <br>
대부분 본인의 설정에 맞게 쓰면 된다. <br>
![sideFix3](/assets/img/postImg/GitHubBlog/createBlog6/sideFix3.JPG) <br>
테마 모드는 라이트와 다크 모드 중 고르는 것인데 비워져있으면 디폴트 값이 라이트 모드다. <br>
avatar가 블로그 프로필 사진이다. 사진이 저장된 경로를 써주면 된다. <br>
이제 사이드바 배경사진으로 넘어가보자 ! <br>

>## <span style='color:#1E90FF'>사이드바 배경 수정하기</span>
<span style='background-color:LavenderBlush; color:red'>_sass 폴더에 addon 폴더에 있는 commons.scss 파일을 열어보자.</span> <br>
여기서 ctrl + F를 이용해 sidebar를 찾자. 아래와 같이 나올 것이다. <br>
![sideFix4](/assets/img/postImg/GitHubBlog/createBlog6/sideFix4.JPG) <br>
빨간 박스 안에 부분만 수정하면 된다. url에 파일의 저장위치를 작성하면 된다. <br>
size의 cover는 배경 이미지가 요소의 전체 영역을 덮도록 이미지의 크기를 조절한다. <br>
position의 center는 배경 이미지의 요소를 가운데에 위치시킨다. <br>
![sideFix5](/assets/img/postImg/GitHubBlog/createBlog6/sideFix5.JPG) <br>
이와 같이 나올 것이다. 사이드바 글꼴색, 호버색이 검정이라 잘 보이지 않아 필자는 위 이미지와 같이 수정했다. <br>

>## <span style='color:#1E90FF'>사이드바 아이콘, 글꼴색 수정하기</span>
글꼴 색과 호버색은 위치를 찾기가 힘들다. 그래서 로컬페이지로 가서 F12를 누른다. <br>
![sideFix6](/assets/img/postImg/GitHubBlog/createBlog6/sideFix6.JPG) <br>
이미지와 같이 1, 2, 3 순으로 진행한다. <br>
<span style='background-color:LavenderBlush; color:red'>_sass 폴더에 addon 폴더에 있는 commons.scss 파일을 열어보자.</span> <br>
그 중 801번 라인으로 가보자. 그럼 아래 이미지와 같이 있을 것이다. <br>
![sideFix7](/assets/img/postImg/GitHubBlog/createBlog6/sideFix7.JPG) <br>
i는 사이드바 글 앞에 있는 아이콘 색깔, span은 글자들의 영역이다. <br>
여기서 color를 본인의 취향에 맞게 설정한다. <br>

><span style='background-color:LavenderBlush; color:red'>_sass 폴더에 addon 폴더에 있는 commons.scss파일을 열어보자</span> <br>
타이틀과 서브타이틀의 색상은 아래 이미지 처럼 a태그와 .site-subtitle에서 수정한다. <br>
![sideFix8](/assets/img/postImg/GitHubBlog/createBlog6/sideFix8.JPG) <br>


>## <span style='color:#1E90FF'>사이드바 호버 배경색 수정하기</span>
<span style='background-color:LavenderBlush; color:red'>_sass폴더 아래 colors폴더안에 typography-light.scss</span>파일을 열어보자. <br>
![sideFix9](/assets/img/postImg/GitHubBlog/createBlog6/sideFix9.JPG) <br>
#으로 색상을 주어도 되고 rgb로 주어도 된다. <br>

>## <span style='color:#1E90FF'>다크모드 사이드바 호버 배경색 수정하기</span>
필자의 사이드바가 우주배경이라 다크모드로 했을 경우 호버색이 어두운색으로 변경되는데 <br>
사이드바 글꼴이 보이지 않아 밝은색으로 변경했다. <br>
<span style='background-color:LavenderBlush; color:red'>_sass폴더 아래 colors폴더안에 typography-dark.scss</span>파일을 열어보자. <br>
![sideFix10](/assets/img/postImg/GitHubBlog/createBlog6/sideFix10.JPG) <br>
라이트모드와 동일하게 변경하면 된다. <br>
색상 변경을 하고 싶었는데 어디있는지 찾지를 못해 하나씩 바꿔가면서 확인했다. 시간 낭비를 너무 했다 ㅠ^ㅠ <br>
이 글을 읽는 방문자들은 이런 일이 없었으면 한다... <br>

>## <span style='color:#1E90FF'>NEXT STEP. </span>
<blockquote class='prompt-tip'>다음 미션은 게시글을 작성해보자.</blockquote>