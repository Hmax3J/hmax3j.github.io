---
title: "[스프링 부트 3 백엔드 개발자 되기 - 자바 편(2판) 스터디] - 1주차 (7.29 ~ 8.4)"
date: 2024-08-05 01:00:00 AM +09:00
categories: [bookStudy, springboot3backend]
tags: [java, study, spring, boot]
---
***

>## <span style='color:#1E90FF'>스프링 부트 3 백엔드 개발자 되기 - 자바 편(2판) 스터디 1주차 </span>
책을 읽고 공부한 내용을 정리하기

>## <span style='color:#1E90FF'>책</span>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000201766024' target='_blank' style='color:red'>스프링 부트 3 백엔드 개발자 되기 - 자바 편(2판)</a> <br>

>## <span style='color:#1E90FF'>클라이언트</span>
- 서버로 요청하는 프로그램 모두를 지칭합니다. <br>
- 웹 브라우저가 대표적인 클라이언트 중 하나입니다. 사용자를 클라이언트라고도 할 수 있겠네요. <br>

>## <span style='color:#1E90FF'>서버</span>
- 서버는 클라이언트의 요청을 받아 처리합니다. <br>
- 클라이언트의 요청을 받으면 서비스, 데이터를 제공하는 컴퓨터 혹은 프로그램이라고 합니다. <br>
- server는 serving과 비슷합니다. 음식점에 갔을 때 음식을 주문하면 <br>
- 완성된 요리를 주문한 사람에게 가져다 주는데 <br>
- 서버도 마찬가지로 클라이언트가 서버에게 나 이거줘라! 요청하면 <br>
- 서버는 알겠어! 여기 있어! 라고 데이터를 전달해주죠! <br>
- 예를 들면 웹툰으로 치면 사용자가 웹 브라우저나 앱에서 웹툰을 보려고 할 때 <br>
- 웹툰 썸네일을 클릭해서 웹툰 목록으로 들어가는데 이 때 썸네일을 클릭 하는 것이 <br>
- 서버에게 나 웹툰 볼거니까 웹툰 목록 좀 보여줘! 라고 서버에게 요청을 하고 <br>
- 서버는 오케이! 여기 목차 있어! 라고 목차를 보여주는 것이 서버의 역할입니다. <br>

>## <span style='color:#1E90FF'>데이터베이스</span>
- 데이터베이스는 체계적이고 구조적으로 데이터를 저장하고 관리하는 일종의 데이터 저장소입니다. <br>
- 다양한 형태의 데이터를 효율적으로 저장하고, 필요할 때 쉽게 접근하고 수정할 수 있도록 도와줍니다. <br>
- 오라클, MySQL 등을 데이터베이스라고 하는데 이런 얘들은 데이터베이스가 아니고 <br>
- 데이터베이스를 관리하는 프로그램입니다. DBMS라고 하죠. 데이터베이스 매니지먼트 시스템(DBMS) <br>
- 동작 원리는 간단합니다! <br>
- 클라이언트에서 SQL(데이터베이스를 조작하기 위한 언어)로 데이터베이스 관리 시스템에 데이터를 요청하면 <br>
- DBMS는 데이터베이스에서 데이터를 꺼내 응답합니다. <br>

>## <span style='color:#1E90FF'>RDB</span>
- Relational Database이고 뜻은 관계형 데이터베이스 입니다. <br>
- 관계형 데이터베이스의 주요 특징이 있습니다.
    - 행(row), 열(col)로 구성된 테이블로 관리한다.
    - 행은 하나의 데이터 레코드이고 열은 데이터 속성을 나타낸다.
    - 기본키를 사용해 각 행을 식별한다.
    - 다른 테이블의 기본키를 참조하여 테이블의 관계를 나타내는 외래키가 있다. <br>
- 더 많은 특징이 있지만 다 적기 힘들어 이 정도만 쓰겠습니다! <br>
- 궁금하면 검색하면 잘 나오니 한 번 찾아보길 추천드립니다! <br>
- RDB에서 유명한 DBMS는 오라클, MySQL, SQL 서버, postgreSQL이 있습니다. <br>

>## <span style='color:#1E90FF'>SQL</span>
- SQL은 Structured Query Language의 약자, 데이터 검색을 하는 언어입니다. <br>
- SQL 뿐만 아니라 ANSI SQL 등 각 RDB별로 있습니다. <br>

>## <span style='color:#1E90FF'>NoSQL</span>
- NoSQL의 뜻이 SQL을 안 쓴다는 의미로 사용되기도 하지만, Not Only SQL의 의미로 많이 사용됩니다. <br>
- RDB는 CRUD가 용이하지만 성능을 올리는게 쉽지 않습니다. <br>
- 성능을 올리려면 머신의 성능을 좋게 하는 스케일업 또는 머신을 여러 대로 분리하는 스케일아웃이 필요합니다. <br>
- 이런 문제들을 해결하기 위해 NoSQL이 등장했습니다. <br>

>## <span style='color:#1E90FF'>아이피(IP)</span>
- 아이피는 인터넷에서 컴퓨터 또는 기기들이 서로 식별하고 통신하기 위한 주소입니다. <br>
- 그래서 아이피를 알면 서버를 찾을 수 있습니다. <br>

>## <span style='color:#1E90FF'>포트</span>
- 포트는 특정 장치 내에서 다양한 서비스를 구분하는 번호입니다 <br>
- 아이피는 인터넷 상에서 특정 장치를 찾아가는 주소입니다. <br>
- 아이피가 도서관의 주소라면 포트는 도서관에서 분류 해놓은 여러 종류의 섹션을 뜻합니다. <br>
- 도서관에 가려면 주소를 알아야 하고 책을 빌리기 위해서는 해당 책이 있는 분야(섹션)에 가야 책이 있습니다. <br>
- 도서관과 섹션을 통해 사람들이 원하는 책을 찾듯이, <br>
- IP 주소와 포트 번호를 통해 인터넷 상에서 원하는 서비스에 접속할 수 있습니다. <br>

>## <span style='color:#1E90FF'>라이브러리와 프레임워크</span>
- 라이브러리는 소프트웨어 개발에서 자주 사용되는 기능이나 코드를 의미합니다.
    - 직접 작성하지 않고도 여러 기능을 사용할 수 있도록 제공되는 일종의 도구입니다.
    - 라이브러리는 특정 기능을 수행하는 도구들의 모음으로, 개발자가 필요할 때 가져다 쓰는 방식입니다.
- 프레임워크는 소프트웨어 개발에서 기본 구조와 아키텍처를 제공하는 일종의 템플릿입니다.
    - 프레임워크는 애플리케이션의 기본적인 구조와 흐름을 정의합니다.
    - 개발자가 이를 기반으로 코드를 작성할 수 있게 합니다.
    - 프레임워크는 소프트웨어 개발에서 중요한 역할을 합니다.
    - 개발자가 애플리케이션을 빠르고 효율적으로 개발할 수 있도록 돕는 기본 구조와 패턴을 제공합니다.