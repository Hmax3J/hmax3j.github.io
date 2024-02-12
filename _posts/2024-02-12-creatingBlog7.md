---
title: "깃허브 블로그 만들기 - Seven"
date: 2024-02-12 07:15:00 PM +09:00
categories: [GitHubBlog]
---
***

>## <span style='color:#1E90FF'>게시글을 써보자.</span>
깃허브 블로그는 GitHub 저장소를 기반으로 마크다운 형식의 파일을 사용하여 게시글을 작성, 관리 할 수 있다. <br>
깃허브 블로그에 게시글을 쓸 때 유의할 점이 몇 가지 있다. 한 번 알아보자. <br>

>## <span style='color:#1E90FF'>게시글을 쓸 때 유의점을 알아보자.</span>
<span style='background-color:LavenderBlush; color:red'>GitHub 블로그 게시글 파일의 이름 형식을 YYYY-MM-DD-title.md로 사용해야 한다.</span> <br>
이유는 게시글을 날짜순으로 정렬하고 쉽게 찾을 수 있도록 하는 것이다. <br>
예를들면 2024-02-12-post.md 이렇게 설정을 해야 한다는 뜻이다. <br>
여기서 post에는 본인이 원하는 제목을 사용하면 된다. <br>
_posts 폴더에 파일 이름 형식에 맞추어 파일을 생성 했으면 이제 게시글을 작성해보자. <br>

>게시글을 쓸 때 Front Matter를 작성해야 한다.
```
---
title: "게시글 제목"
date: YYYY-MM-DD 00:00:00 PM +09:00
categories: [categories1, categories2]
tags: [tags1, tags2]
---
```
이런 식으로 작성하면 된다. 아래 예시 게시글을 한 번 보자. <br>
![posting1](/assets/img/postImg/GitHubBlog/createBlog7/posting1.JPG) <br>
1은 Front Matter에서 작성한 title이다. <br>
2는 작성한 시간이다. 현재 시간이 2024년 2월 12일 저녁 11시라면 저녁 12시로 설정할 경우 에러가 난다. <br>
즉 미래의 시간으로 작성을 할 수 없다는 뜻이다. <br>
시간은 12시간, 24시간으로 설정해도 된다. 필자는 12시간으로 작성한다. <br>
12시간으로 작성할 경우 시간을 작성하고 뒤에 AM 또는 PM을 작성해주면 된다. <br>
깃허브 블로그에서는 기본적으로 UTC 시간을 사용하기 때문에 +09:00을 해야 한국 시간에 맞추어 진다. <br>
3은 본인이 작성할 게시글 내용이다. <br>
4는 이미지 파일을 삽입한 것이다. 이미지 파일은 아래 코드 처럼 작성하면 된다. <br>
```
![대체텍스트](이미지가 저장된 경로)
![postEx](/assets/img/postImg/GitHubBlog/createBlog7/githubex.jpg)
```
대체 텍스트란 이미지를 불러오지 못했을 때 나타나는 메세지다. <br>
5는 말 그대로 게시글이 속한 카테고리다. 아래 예시를 보자. <br>
![posting2](/assets/img/postImg/GitHubBlog/createBlog7/posting2.JPG) <br>
이렇게 카테고리에 속하게 된다. <br>
6은 태그다. 태그를 클릭하면 태그에 해당하는 내용들의 게시글이 나타난다. <br>

>## <span style='color:#1E90FF'>예시로 작성한 게시글을 살펴보자.</span>
아래 사진은 필자가 예시로 작성한 글이다. 이런 식으로 작성하면 된다. <br>
![posting3](/assets/img/postImg/GitHubBlog/createBlog7/posting3.JPG) <br>
이렇게 게시글 까지 작성해 보았다. 이제 진짜 끝이 보이는 것 같다. <br>
깃허브 블로그 만드는 매뉴얼 작성이 이렇게 오래 걸릴지 몰랐다 ㅠㅠ <br>
좀 더 스피드하게 진행해야겠다. <br>

>## <span style='color:#1E90FF'>NEXT STEP. </span>
<blockquote class='prompt-tip'>다음 미션은 구글에 검색 했을 때 내 블로그가 다른 사람에게 노출되게 해보자.</blockquote>