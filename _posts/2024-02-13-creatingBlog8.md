---
title: "깃허브 블로그 만들기 - Eight"
date: 2024-02-13 01:59:00 AM +09:00
categories: [GitHubBlog]
---
***

>## <span style='color:#1E90FF'>검색 엔진에 블로그를 노출시켜보자.</span>
드디어 고지가 보인다. 드디어 이 단계 까지 왔다. <br>
블로그를 만들었고 게시글을 작성했으면 다른 방문자들이 내 글을 읽을 수 있어야 한다. <br>
내 글을 읽을 수 있도록 검색 엔진에 내 블로그를 노출 시켜보도록 하자. <br>

>## <span style='color:#1E90FF'>sitemap.xml을 생성해보자.</span>
sitemap은 웹 사이트의 페이지 구조 및 갱신 정보를 검색 엔진에게 제공하기 위한 XML 형식의 파일이다. <br>
검색 엔진이 웹 페이지를 효율적으로 크롤링하고, 검색 결과를 업데이트하는 데 도움을 준다. <br>
그래서 깃허브 블로그를 검색 엔진에 노출하려면 sitemap.xml을 생성해야 한다. <br>
루트 디렉토리에 sitemap.xml 이름의 파일을 생성한다. <br>
그리고 링크된 <a href='https://github.com/hmax3j/hmax3j.github.io/blob/main/sitemap.xml' target='_blank' style='color:red'>이 코드</a>를 붙여넣는다. <br>
로컬서버에서 sitemap.xml을 확인한다. <br>
![searchBlog1](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog1.JPG) <br>
위 이미지처럼 나온다면 정상적으로 생성이 완료되었다. <br>

>## <span style='color:#1E90FF'>robots.txt를 생성해보자.</span>
robots.txt은 검색 엔진에게 어떤 부분을 크롤링하고 어떤 부분은 크롤링하지 말아야 하는지를 명시할 수 있다. <br>
루트 디렉토리에 robots.txt 파일을 생성하자. 그 이후 아래 코드를 붙여넣자. <br>
```
User-agent: *
Allow: /
Sitemap: https://hmax3j.github.io/sitemap.xml
```
여기서 sitemap은 본인의 블로그 주소를 입력해야 한다. <br>

>## <span style='color:#1E90FF'>feed.xml을 생성해보자.</span>
feed.xml은 블로그의 RSS(Really Simple Syndication) 피드를 생성하는 역할을 한다. <br>
구독자들이 블로그의 컨텐츠를 쉽게 볼 수 있게 만든다. <br>
루트 디렉토리에 feed.xml을 생성하자. 그리고 링크된 <a href='https://github.com/hmax3j/hmax3j.github.io/blob/main/feed.xml' target='_blank' style='color:red'>이 코드</a>를 붙여넣는다. <br>
이렇게 3개의 파일을 생성했으면 검색 엔진에 노출 시키기 전 준비는 모두 끝났다. <br>
이제 본격적으로 검색 엔진에 블로그를 등록해보자. <br>

>## <span style='color:#1E90FF'>Google Search Console에 등록해보자.</span>
<a href='https://search.google.com/search-console/about' target='_blank' style='color:red'>Google Search Console</a>에 접속해 시작하기를 누른다. <br>
![searchBlog2](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog2.JPG) <br>
위 이미지 처럼 나타나는데 우리는 URL 접두어를 사용한다. 깃허브 블로그 주소를 쓰고 계속을 누른다. <br>
![searchBlog3](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog3.JPG) <br>
위 이미지에 나오는 안내사항을 따라 진행한다. 이 때 html을 루트 디렉토리에 위치시킨다. <br>
그리고 깃허브 레포지토리에 push를 해야 소유권 인증이 된다. 안하면 자꾸 실패가 뜬다. <br>
![searchBlog4](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog4.JPG) <br>
로컬 서버에서 테스트를 한다. 소유권 확인이 끝나면 Google Search Console로 이동한다. <br>
![searchBlog5](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog5.JPG) <br>
sitemap을 클릭해서 이동한다. <br>
![searchBlog6](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog6.JPG) <br>
새 사이트맵 추가에 사이트맵 URL을 작성한다. 루트 디렉토리에 저장했으니 sitemap.xml만 입력하고 제출한다. <br>
![searchBlog7](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog7.JPG) <br>
위와 같이 나타난다. 시간이 지나야 등록이 된다고 한다. <br>
얼마의 시간을 기다려야 할 지 모르겠다 ㅠ^ㅠ 빨리 등록되면 좋겠다. 가슴이 두근두근 하는고만 ! <br>
다음은 Naver에 등록해보자. <br>

>## <span style='color:#1E90FF'>Naver에 등록해보자.</span>
<a href='https://searchadvisor.naver.com/' target='_blank' style='color:red'>Naver Search Advisor</a>에 접속하자. <br>
![searchBlog8](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog8.JPG) <br>
웹 마스터 도구를 클릭하자. <br>
![searchBlog9](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog9.JPG) <br>
블로그 주소를 입력한 후 제출을 한다. <br>
![searchBlog10](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog10.JPG) <br>
구글 등록할 때와 마찬가지로 html을 다운 받아서 루트 디렉토리에 위치시킨다. <br>
![searchBlog11](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog11.JPG) <br>
로컬 서버에서 html파일을 테스트한다. 그리고 레포지토리에 push 한다. <br>
![searchBlog12](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog12.JPG) <br>
소유권 확인이 끝나면 위 이미지 처럼 등록이 되어 있다. 이제 사이트맵 제출을 해보자. <br>
등록된 사이트 목록을 클릭하자. <br>
![searchBlog13](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog13.JPG) <br>
요청에 사이트맵 제출을 클릭한다. sitemap.xml 주소를 입력하고 확인을 클릭한다. <br>
제출된 사이트맵에 잘 등록이 되어있는지 확인한다. <br>
이렇게 Naver 검색 엔진에도 등록했다. 다음은 Daum에 등록해보자. <br>

>## <span style='color:#1E90FF'>Daum에 등록해보자.</span>
<a href='https://register.search.daum.net/index.daum' target='_blank' style='color:red'>Daum 검색등록</a>에 접속하자. <br>
![searchBlog14](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog14.JPG) <br>
등록에 블로그 등록을 클릭한 후 블로그 주소를 입력하고 확인을 누른다. <br>
![searchBlog15](/assets/img/postImg/GitHubBlog/createBlog8/searchBlog15.JPG) <br>
위 이미지와 같이 등록이 끝났다. <br>
이렇게 Google, Naver, Daum에 블로그를 등록했다. <br>

>## <span style='color:#1E90FF'>FINALLY</span>
드디어 깃허브 블로그 만들기의 대장정이 끝났다. <br>
정말 쉽지 않은 미션이었다. 쉽게 만들 수 있을 것 같았지만 전혀 아니었다. <br>
에러부터 포스팅까지... 특히 에러 해결에 시간이 오래 걸려 힘들었다. <br>
그래도 이렇게 포스팅 까지 마치고 나니 뿌듯하다.
다음은 포트폴리오를 정리한 후 포스팅 할 예정이다. <br>
이렇게 첫 번째 주제로 깃허브 블로그 만들기를 끝내도록 하겠다. <br>
앞으로도 이 뿌듯함과 성취감을 잊지말고 꾸준하게 블로그를 관리해야겠다. <br>
이 글을 읽는 방문자들은 깃허브 블로그를 만들 의향이 있다면 필자처럼 고생하지말고 <br>
쉽고 빠르게 스트레스 없이 만들었으면 좋겠다. <br>
개발의 고수가 될 그 날 까지 항상 빠이팅있게 달려가겠다. 모두들 빠이팅 !!