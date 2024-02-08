---
title: "깃허브 블로그 만들기 - Two"
date: 2024-02-08 11:56:00 +09:00
categories: [GitHubBlog]
---
***

>## <span style='color:#1E90FF'>보기 좋은 떡이 먹기도 좋다.</span>
보기 좋은 떡이 먹기도 좋다. 라는 속담이 있듯이 <br>
필자는 블로그도 외관이 예뻐야 블로그 관리하는 맛이 있을 거라 생각한다. <br>
처음엔 블로그 테마를 내가 예쁘게 만들어보자. 라고 생각했다. <br>
그러나, 한 번 훑어보고 생각만 하기로 했다... <br>
~~필자의 미적 감각은 지극히 개발자적인 특징을 갖고 있었기 때문이다;;~~ <br>
그래서 찾아보고 알게 된 것이 <span style='color:red'>Jekyll 테마</span>이다. <br>
Jekyll 테마를 찾아보면 유명한 블로그 테마도 많고 예쁜 것도 많다. <br>
그 중에 유료 테마, 무료 테마가 있다. <br>
필자는 많은 사람들이 사용하고 있는 무료 chirpy 테마로 선택했따 ! <br>
<span style='color:red'>Jekyll</span>은 <span style='color:red'>Ruby</span> 기반으로 만들어진 정적 사이트 생성기다. <br>
그래서 Jekyll 테마를 이용하려면 Ruby를 먼저 설치해야 한다. <br>

>## <span style='color:#1E90FF'>Ruby 설치하기</span>
<a href='https://rubyinstaller.org/downloads/' target='_blank' style='color:red'>Ruby 다운로드</a>에 가서 Ruby를 다운로드 한다. <br>
필자는 구글링 해보니 지킬이 32비트기반이라 루비도 32비트로 다운받으라 해서 다운해서 사용하고 있었다. <br>
하지만 컴퓨터는 window 10, 64비트인데 나중에 뭔가 문제가 생기지 않을까 싶어 우리의 구원 GPT에게 물어봤다. <br>
GPT는 작은 블로그나 프로젝트에서는 문제가 생기지 않을 것이라 했다. <br>
그리고 가능하면 64비트로 사용하라해서 이번 포스팅을 작성하면서 루비와 지킬을 64비트로 바꾸어보았다. <br>
<span style='color:red'>Ruby+Devkit 3.2.3-1 (x64)</span>으로 다운 받아서 실행했다. <br>

>![downRuby1](/assets/img/postImg/GitHubBlog/createBlog2/ruby64Download1.JPG) <br>
1.Next를 누른다. <br>

>![downRuby2](/assets/img/postImg/GitHubBlog/createBlog2/ruby64Download2.JPG) <br>
2.다운받을 위치를 선택 및 체크박스 모두 체크 후 Install을 한다.

>![downRuby3](/assets/img/postImg/GitHubBlog/createBlog2/ruby64Download3.JPG) <br>
3.Next를 누른다. <br>

>![downRuby4](/assets/img/postImg/GitHubBlog/createBlog2/ruby64Download4.JPG) <br>
4.Finish를 누른다. <br>

>![downRuby5](/assets/img/postImg/GitHubBlog/createBlog2/ruby64Download5.JPG) <br>
5.Finish를 누르면 자동으로 프롬프트가 실행된다. 여기서 ENTER를 누른다. <br>
필자는 여기서 루비를 삭제 및 설치를 몇 번이나 반복했다. <br>
설치가 안되는 이유를 몰랐고 몇 번을 해도 계속 안되니 깃허브 블로그 만드는 것을 포기하고 싶었다.. <br>
하지만 불굴의 사나이, <span style='background-color:PaleGreen; color:red'>중요한 것은 꺾이지 않는 마음..! 중꺾마의 마인드</span>를 가지고 한참을 검색했다. <br>
나는 답을 찾을 것이다. 언제나 그랬듯이. <br>
결국 찾아내고야 말았다. <br>
설치가 안되었던 이유는 PC에 저장된 이름이 <span style='color:red'>한글</span>이었기 때문이다... <br>
한글은 위대한데 환경이 따라주지 않는다. 너무 슬프다. <br>
<span style='background-color:LavenderBlush; color:red'>PC이름이 한글이면 설치를 하다가 한글인식을 못해 설치가 안된다.</span> <br>
PC이름은 영어로 해야 하는 것을 이번에 뼈저리게 느꼈다. <br>
32비트 설치 할 때 이미 해결을 해서 64비트 설치 할 때는 문제 없이 넘어갔지만 <br>
만약 <span style='background-color:LavenderBlush; color:red'>PC이름이 한글이라면... PC이름을 영어로 변경해야 한다.</span> <br>
변경하는 방법은 <a href='https://blog.naver.com/PostView.naver?blogId=rkdalstj7504&logNo=222173490548' target='_blank' style='color:red'>여기</a> 리라님의 블로그를 참고하도록 하자. <br>

>![downRuby6](/assets/img/postImg/GitHubBlog/createBlog2/ruby64Download6.JPG) <br>
6.ENTER를 누른다. <br>

>![downRuby7](/assets/img/postImg/GitHubBlog/createBlog2/ruby64Download7.JPG) <br>
7.Ruby 설치가 완료되었다. 프롬프트에서 <span style='background-color:LavenderBlush; color:red'>ruby -v</span>를 입력해 루비 버전을 확인한다.<br>
Ruby 버전이 정상적으로 출력된다면 설치가 완료된 것이다. <br>
다음은 Jekyll 설치하는 방법이다. <br>

>## <span style='color:#1E90FF'>Jekyll 설치하기</span>
프롬프트에서 루비 명령어인 gem을 이용해 jekyll과 bundler를 설치하자. <br>
gem: RubyGems라는 Ruby 패키지 저장소에서 Ruby 라이브러리 및 도구를 설치하고 관리하는 명령어이다. <br>

>![downJekyll1](/assets/img/postImg/GitHubBlog/createBlog2/jekyllDownload1.JPG)
1.프롬프트에서 <span style='background-color:LavenderBlush; color:red'>gem install jekyll bundler</span>를 입력하자. <br>

>![downJekyll2](/assets/img/postImg/GitHubBlog/createBlog2/jekyllDownload2.JPG)
2.jekyll이 잘 설치되었는지 <span style='background-color:LavenderBlush; color:red'>jekyll -v</span>를 입력해 확인하자. <br>
위 이미지를 보다시피 뭔가 이상했다. 그래서 bundle install 해봤더니 gemfile이 없다고 한다. 당황스러웠다.. <br>
jekyll serve를 실행해 보았는데도 실행이 안되었다. <br>

>![downJekyll3](/assets/img/postImg/GitHubBlog/createBlog2/jekyllDownload3.JPG)
혹시나 싶어 블로그 repo로 이동해 실행해 보았다. <br>
bundle install이 안되었다고 서버 작동에 실패했다. 그래서 bundle install을 했다. 다행히 성공..!! <br>
3.폴더 이동 후 <span style='background-color:LavenderBlush; color:red'>bundle install</span>을 입력하자. <br>
install이 완료된 후 jekyll version을 확인해보니 2번에서 출력됐던 것과 달랐다. 느낌이 좋았다.

>![downJekyll4](/assets/img/postImg/GitHubBlog/createBlog2/jekyllDownload4.JPG)
4.프롬프트에서 <span style='background-color:LavenderBlush; color:red'>jekyll serve</span>를 실행하자. <br>
jekyll serve와 bundle exec jekyll serve 둘 다 서버가 실행이 되었다. <br>
두 개의 명령어가 무엇이 다른지 궁금해 찾아 보았다. <br>
<span style='background-color:LavenderBlush; color:red'>jekyll serve</span>는 시스템 전역의 Jekyll을 사용하여 빌드하고 실행한다. <br>
시스템에 전역으로 설치된 Jekyll 버전을 사용하게 되는데, <br>
이는 로컬 프로젝트에 필요한 의존성 버전과 일치하지 않을 수 있다. <br>
로컬 프로젝트가 특정한 Jekyll 버전에 의존하지 않고, 시스템 전역의 Jekyll을 사용하는 경우에 사용된다. <br>
<span style='background-color:LavenderBlush; color:red'>bundle exec jekyll serve</span>는 Bundler를 통해 프로젝트 내에 설치된 Jekyll을 사용하여 빌드하고 실행한다. <br>
bundle exec를 사용함으로써 현재 프로젝트의 Gemfile에 명시된 의존성을 사용하게 된다. <br>
따라서 프로젝트의 Jekyll 버전과 의존성이 일치한다. <br>
일반적으로 프로젝트에 로컬로 설치된 Jekyll을 사용하고자 할 때 사용된다. <br>
gemfile.lock에 의존성 정보를 저장하는데 bundle install을 통해 생성된다. <br>
gemfile을 사용하는 이유는 일관성 유지, 버전 충돌 방지 등이 있다. <br>
앞으로는 jekyll serve 대신 bundle exec 를 사용해야겠다. <br>

>5.jekyll serve 실행 시 적용된 address <br>
<span style='background-color:LavenderBlush; color:red'>127.0.0.1:4000</span>을 브라우저 주소창에 입력하면 아래 이미지와 비슷한 내용의 홈페이지가 나타난다. <br>
![downJekyll5](/assets/img/postImg/GitHubBlog/createBlog2/jekyllDownload5.JPG) <br>
필자는 이미 블로그를 만들어버려서 jekyll 초기 화면이 없어 구글의 이미지를 발췌했다. <br>
위 이미지의 출처는 <a href='https://opensource.com/article/21/9/build-website-jekyll' target='_blank' style='color:red'>여기</a> 다. <br>
여기까지의 미션이 블로그 테마를 적용하기 전에 해야하는 필수 미션이다. <br>

>## <span style='color:#1E90FF'>NEXT STEP.</span>
<blockquote class='prompt-tip'>다음 미션은 블로그에 테마를 적용해보자.</blockquote>