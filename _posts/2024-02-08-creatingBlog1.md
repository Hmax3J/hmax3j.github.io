---
title: "깃허브 블로그 만들기 - First"
date: 2024-02-08 02:26:00 +09:00
categories: [GitHubBlog]
---
***
># <span style='background-color:#483D8B; color:tomato'>깃허브 블로그를 만들기까지의 과정</span>
만들고나서 처음으로 포스팅을 하게 되었는데 정말 힘겹게 첫 포스팅을 하게 되었다. <br>
이 글을 보게 될 방문자들은 이런 상황을 겪지 않고 쉽게 만들었으면 해서 게시글을 남기게 되었다. <br>
<span style='color:red'>Windows</span> 기준으로 작성되었다. 그럼 시작해보자. <br>

>## <span style='color:#1E90FF'>시작은 Repositories 생성 </span>
깃허브 블로그의 장점은 커스터마이징, 깃허브 기능 활용, 무료 제공 등이 있다. <br>
깃허브 블로그를 만들기 위해서는 깃허브의 Repositories에 블로그 전용 Repositories를 생성해야 한다. <br>
Repositories를 생성하는 이유는 깃허브 페이지를 활용하여 정적인 웹사이트를 호스팅하기 위해서다. <br>
먼저 본인 깃허브의 Repositories에 들어가서 <span style='color:red'>New</span>를 클릭한다. <br>
New를 클릭하면 아래와 같은 이미지의 내용이 나오게 된다. <br>
![gitrepo](/assets/img/postImg/GitHubBlog/gitRepoCreate.JPG)
<span style='color:MediumSeaGreen'>Repository name</span>: 왼쪽에 있는 Owner 이름과 같게 만들어야 한다. <span style='color:red'>{OwnerName}.github.io</span>로 적어주자.<br>
필자는 이미 만들었기 때문에 빨간 글씨가 나타나지만 만들어져 있지 않으면 아래 이미지 처럼 초록글씨가 나타난다. <br>
![gitrepo2](/assets/img/postImg/GitHubBlog/gitRepoCreate2.JPG) <br>
<span style='color:MediumSeaGreen'>Public / Private</span>: 저장소 공개, 비공개 설정 하는 부분이다. public 으로 하자. <br>
<span style='background-color:LavenderBlush; color:Red'>public으로 해야 블로그 컨텐츠를 다른 사람이 볼 수 있다.</span> <br>
<span style='color:MediumSeaGreen'>Add a README file</span>: README.md 파일 생성 여부를 묻는다. 설명서처럼 활용할 수 있다. <br>
위의 3가지를 다 작성했으면 <span style='color:red'>Create repository</span>을 하자. <br>
생성된 {OwnerName}.github.io Repository로 가면 README.md 파일만 있을 것이다. <br>
여기서 아래의 이미지 처럼 오른쪽에 있는 Code를 클릭하고 Download.Zip을 한다. <br>
![repoClone](/assets/img/postImg/GitHubBlog/repoClone.JPG) <br>
Download.Zip한 파일의 압축을 푼 후 본인이 원하는 위치에 폴더를 이동한다. <br>
cmd에서 git clone을 해도 되지만 압축해제 하는 것이 더 편한 것 같아 Zip으로 clone했다. <br>
필자는 C:/dev/blog/Hmax3J.github.io 여기에 만들었다. <br>
여기까지 되었다면 첫 번째 미션은 끝났다. <br>

>## <span style='color:#1E90FF'>Next STEP. </span>
다음 미션은 블로그에 테마를 적용하는 방법이다. <br>