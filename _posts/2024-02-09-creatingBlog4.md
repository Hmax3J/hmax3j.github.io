---
title: "깃허브 블로그 만들기 - Four"
date: 2024-02-09 00:00:00 AM +09:00
categories: [GitHubBlog]
---
***

>## <span style='color:#1E90FF'>테마 적용 후 설정</span>
블로그에 테마를 설정하고 난 뒤 정상적으로 되었는지 확인을 해보자. <br>
<span style='background-color:LavenderBlush; color:red'>Window 사용자는 안된 것이 분명 있을 것이다..</span> <br>

>1.로컬 홈페이지에 접속해 테마모드를 눌러보거나 사이드바를 클릭한 후 프롬프트 창을 한 번 보자. <br>
![gitSet1](/assets/img/postImg/GitHubBlog/createBlog4/gitHubSetting1.JPG) <br>
위 이미지 처럼 assets/js/dist에 js 파일이 없다고 뜰 것이다. <br>
필자는 이 부분을 못보고 블로그의 다크모드가 적용이 안되어 이유를 한참을 구글링했다. <br>
여기서 두 번째의 위기가 찾아왔다. 정말 정말 깃허브 블로그 안해 !! 할 뻔 했다. <br>
하지만, 나 ! Vincent는 불굴의 사나이... 중꺾마의 마인드를 다시 한 번 새기고 차근차근 확인했다. <br>
결국 언제나 그랬듯 답을 찾아냈다. 바로 위의 설명처럼 js파일이 없었던 것이다. <br>
왜 js파일이 없었는가 찾아봤는데 Window에서는 <span style='background-color:LavenderBlush; color:red'>bash tools/init</span>을 안해서 그렇다고 한다. <br>
init은 맥이나 리눅스에서 가능하다고 한다. 이에 관한 것은 잠시후 다시 적겠다.<br>

>2.js파일을 다운로드 받아보자. <br>
js파일을 다운 받으려면 <span style='background-color:LavenderBlush; color:red'>NODE_ENV=production npx rollup -c --bundleConfigAsCjs</span> 코드를 실행해야 한다. <br>
어떻게 실행하느냐... 필자는 여기서 또 엄청 헤맸다 ㅠ^ㅠ <br>
![gitSet2](/assets/img/postImg/GitHubBlog/createBlog4/gitHubSetting2.JPG) <br>
위 이미지처럼 cmd에서 바로 명령어를 입력하면 실행을 할 수 없다. <br>
왜 그런지 찾아봤더니 환경 변수 설정 차이, 명령어 해석 차이, 패스 설정 등이 있었다. <br>
cmd말고 <span style='color:red'>Git bash</span> 에서 <span style='background-color:LavenderBlush; color:red'>NODE_ENV=production npx rollup -c --bundleConfigAsCjs</span>코드를 실행하니 되었다. <br>
![gitSet3](/assets/img/postImg/GitHubBlog/createBlog4/gitHubSetting3.JPG) <br>
여기서 cmd에서는 왜 안될까 찾아봤는데 환경 변수 설정 차이가 문제인 것 같았다. <br>
cmd는 <span style='color:red'>set</span> NODE_ENV=production을 사용하고, Bash에서는 <span style='color:red'>export</span> NODE_ENV=production을 사용한다. <br>
여기서 필자는 cmd는 왜 set을 하고 git bash는 바로 실행이 가능한가 궁금해서 찾아봤다. <br>
결론은 <span style='background-color:LavenderBlush; color:red'>Git Bash는 Bash 스크립트 문법을 따르기 때문에 Bash에서 사용되는 인라인 환경 변수 설정이 가능하며, <br> 이로 인해 해당 명령어를 바로 실행할 수 있는 것이다.</span> <br>
cmd에서 set을 이용하면 되는지 확인을 해보았다. <br>
![gitSet4](/assets/img/postImg/GitHubBlog/createBlog4/gitHubSetting4.JPG) <br>
위 이미지의 노란색 부분이 바로 명령어를 실행한 부분이고, <br>
보라색 부분이 set으로 환경 변수를 설정하고 실행한 부분이다. <br>
보라색 부분이 에러가 났지만 딱 보아도 차이가 있지 않은가 ? <br>
여기서 cmd와 bash의 차이를 알게 되었고, 까먹지 않도록 해야겠다. <br>

>## <span style='color:#1E90FF'>이제는 진짜 테마 적용이 끝난거지 ?</span>
라고 생각하면 필자와 아주 서먹서먹한 사이가 될 것이다. <br>
왜냐하면, 우리는 바로 Windows를 사용하고 있지 않은가 ? <br>
그렇다... Mac에서는 bash tools/init을 하면 자동으로 다 된다고 하던데.. ~~사실 잘 모름;;~~ <br>
Windows.. 사람을 강하게 키우는구나.. <br>
우리 Windows 용사들이여, 우리는 init을 하지 않았기 때문에 직접 파일 수정을 해야 한다 ! <br>
아래 파일들을 삭제해보자. <br>
<span style='background-color:LavenderBlush; color:red'>.travis.yml</span> 필자는 없었다. <br>
<span style='background-color:LavenderBlush; color:red'>_posts 폴더 하위의 파일들</span> chirpy에서 샘플로 제공해주는 post다. 필요없으면 삭제한다. <br>
<span style='background-color:LavenderBlush; color:red'>docs 폴더</span>를 어디 옮겨놨는데 어디에 옮긴지 찾지 못했다. 아직까지 문제는 없는 것 같다. <br>
<span style='background-color:LavenderBlush; color:red'>.github 폴더</span>에서
<span style='color:red'>workflows 폴더</span>를 제외하고 다 삭제한다. <br>
<span style='background-color:LavenderBlush; color:red'>.github/workflows/</span>에서
<span style='color:red'>commitlint.yml</span>,
<span style='color:red'>page-deploy.yml.hook</span>를 제외하고 다 삭제한다. <br>
<span style='background-color:LavenderBlush; color:red'>page-deploy.yml.hook</span>에서
<span style='color:red'>.hook</span>을 지운다. <br>

>![gitSet5](/assets/img/postImg/GitHubBlog/createBlog4/gitHubSetting5.JPG) <br>
page-deploy.yml 파일을 실행해 들어가면 <br>
상단 부분에 위 이미지의 빨간 박스처럼 브랜치가 main, master 2개가 적혀있다. <br>
여기서 본인의 브렌치와 맞지 않는 것을 주석처리 한다. <br>
![gitSet6](/assets/img/postImg/GitHubBlog/createBlog4/gitHubSetting6.JPG) <br>
필자는 main이라 master를 주석처리 했다. <br>
파일 초기화 및 설정은 거의 다 했다. 하지만 아직 많이 남았다...<br>
깃허브 블로그 진짜 힘들구나 싶었다. 사람들이 다른 블로그 플랫폼을 쓰는 것이 이해가 되었다. <br>
이제 깃 액션을 이용해 빌드와 배포를 하면 거의 마지막이 될 것 같다. 찐막 !!! <br>
이 부분은 다음 미션으로 넘기겠다. <br>

>## <span style='color:#1E90FF'>NEXT STEP.</span>
<blockquote class='prompt-tip'>다음 미션은 빌드와 배포를 해보자.</blockquote>