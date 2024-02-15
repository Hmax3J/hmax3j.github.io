---
title: "Portfolio - MovieCommunitySite"
date: 2024-02-15 03:50:00 AM +09:00
categories: [Portfolio, MovieCommunitySite]
---
***

># Movie Community - 영화 커뮤니티 프로젝트
**Movie Community**는 영화에 관한 소통과 공유를 중심으로 하는 영화 커뮤니티 웹 사이트입니다. 사용자들은 영화에 대한 의견을 나누고, 추천을 받을 수 있으며, 특정 요일이나 조건에 따라 개인 맞춤형 추천 서비스를 이용할 수 있습니다. 또한 영화 검색과 리뷰 기능을 통해 다양한 영화 정보를 찾고 공유할 수 있습니다.

>## 주요 기능
>> **영화 토론과 추천**
   - 사용자들은 영화에 대한 토론을 자유롭게 할 수 있습니다.
   - 특정 요일마다 추천되는 영화를 확인하고, 사용자 개인의 취향에 맞는 영화를 추천 받을 수 있습니다.

>> **영화 검색**
   - 웹 사이트 내에서 영화를 검색하여 자세한 정보를 확인할 수 있습니다.
   - 검색 결과를 다양한 기준으로 필터링하여 사용자 편의에 맞게 제공됩니다.

>> **영화 리뷰 기능**
   - 사용자들은 영화에 대한 리뷰를 작성하고 다른 사용자들과 공유할 수 있습니다.
   - 리뷰는 별점과 함께 제공되어 사용자들이 평가를 쉽게 확인할 수 있습니다.

>## 기술 스택
>> **백엔드**
   - **Spring Boot**
   - **Spring**
   - **Java**
   - **MyBatis**

>> **프론트엔드**
   - **JavaScript**
   - **jQuery**
   - **CSS 및 Bootstrap**
   - **HTML**

>> **데이터베이스**
   - **Oracle DB**

>> **웹 서버**
   - **Apache Tomcat**

>## 개발 과정과 역할
프로젝트 개발 과정 팀장 역할 수행 및 업무 진행
>> **프로젝트 관리**
   - 깃허브를 활용한 버전 관리 및 이슈 트래킹으로 팀원들과의 협업
   - 스프린트 계획 및 회고를 통해 프로젝트 일정을 관리, 팀원 간의 원활한 소통 유지

>> **팀원 역할 분담**
   - 팀원 역할과 책임 분담으로 효율적인 개발 진행
   - 코드 리뷰 및 팀원 간의 지식 공유를 통해 코드 품질 향상

>> **개발**
   - 주요 회원 기능과 게시판 기능 구현
   - Spring Boot, MyBatis를 활용하여 안정적이고 효율적인 백엔드 구조 구축

>## 기능 구현
>> **로그인**
   - 입력 정보 전송 -> 서버 -> 데이터베이스 매칭 -> 인증 성공 수행 <br>
   　　　　　　　　　데이터베이스 매칭 실패 -> 인증 실패 수행
   - 코드: RESTful API 'POST' 구현
```java
@PostMapping("login")
public User login(@RequestBody User userLogin, HttpSession session) {
	User user = userService.loginValidate(userLogin);
	if(user != null) {
		    session.setAttribute("userId", user.getUserId());
		    session.setAttribute("userNum", user.getUserNum());
	}
	return user;
}
```
   - 설명: 로그인은 상태 변경 동작이라 명확하게 나타내기 위해 REST API 사용 <br>
   - 개선점 1. 비밀번호 해시처리 필요 -> Spring Security || 해시 함수 구현을 통해 개선 가능 <br>
   　　　2. 토큰 기반의 인증 방식 도입시 세션보다 더욱 단순하게 관리 가능 -> JWT 활용으로 개선 가능 <br>
   　　　3. 응답 형식 표준화 필요 -> ResponseEntity로 상태 코드, 메시지 명시적 반환으로 개선 가능 <br>
   　　　4. HTTPS 사용 고려 -> 데이터 암호화로 데이터 변조나 도청을 방지, SEO 이점 <br>

>> **로그아웃**
   - 로그아웃 -> 세션 종료, 로그인 상태 해제 -> 리다이렉트 <br>
   - 코드:
```java
@GetMapping("/logout")
public ModelAndView logout(ModelAndView mv, HttpSession session) {
    session.invalidate();
    mv.setViewName("redirect:/");
	return mv;
}
```
   - 설명: REST API 사용 <br>
   - 개선점 1. GET은 보안에 취약 -> POST 메서드 사용으로 개선 가능 <br>
   　　　2. 간소화 가능 -> 반환 타입 String으로 개선 가능 <br>
```java
@PostMapping("/logout")
public String logout(HttpSession session) {
    session.invalidate();
    return "redirect:/";
}
```

>> **회원가입**
   - 입력 정보 전송 -> 서버 -> 데이터베이스 매칭 -> 인증 성공 수행 <br>
   　　　　　　　　　데이터베이스 매칭 실패 -> 인증 실패 수행
   - 코드:
```java
@PostMapping("addUser")
public void addUser(@RequestBody UserGenre userGenre) {
	User user = userGenre.getUser();
	userService.addUser(user);
	User userNum = userService.getUser(user.getUserId());
	List<Integer> genres = userGenre.getGenreNum();
	for(int genre: genres) {
		    userService.addUserGenre(userNum.getUserNum(), genre);
	}
}
```
   - 설명: REST API 사용, 선호장르는 없음, 단수, 복수 입력가능 <br>
   - 개선점 1. 동시성 측면 고려 -> 트랜젝션 관리, 비지니스 로직을 서비스계층으로 분리로 개선 가능 <br>
```java
UserController 작성
@PostMapping("addUser")
public void addUser(@RequestBody UserGenre userGenre) {
    User user = userGenre.getUser();
    userService.addUser(user);
    List<Integer> genres = userGenre.getGenreNum(); // 사용자 추가 후 바로 장르 추가
    userService.addUserGenres(user.getUserId(), genres);
} // UserController 비지니스 로직 제거
```
```java
UserServiceImpl 작성
@Override
@Transactional
public void addUserGenres(String userId, List<Integer> genreNums) {
    User user = getUser(userId);
    int userNum = user.getUserNum();
    for (int genre : genreNums) {
                addUserGenre(userNum, genre);
    } // 비지니스 로직 추가
}
```
```java
UserServiceImpl 작성
@Override
@Transactional
public void addUserGenre(int userNum, int genreNum) {
    try {
            // 데이터베이스 연결 및 트랜잭션 시작
            Connection connection = // 데이터베이스 연결 객체 생성
            connection.setAutoCommit(false); // 트랜잭션 시작
            // SQL 쿼리를 사용하여 사용자와 장르 간의 관계 추가
            String query = "INSERT INTO UserGenre (userNum, genreNum) VALUES (?, ?)";
        try (PreparedStatement preparedStatement = connection.prepareStatement(query)) {
                    preparedStatement.setInt(1, userNum);
                    preparedStatement.setInt(2, genreNum);
                    preparedStatement.executeUpdate();
        }
            connection.commit(); // 트랜잭션 커밋
    } catch (SQLException e) {
            connection.rollback(); // 예외 발생 시 롤백
            e.printStackTrace(); // 예외 처리는 적절하게 수행
    } finally {
            connection.close(); // 데이터베이스 연결 종료
    }
}
```

>> **마이페이지**
   - 사용자 정보 조회 -> 뷰 전달 -> 사용자 정보 출력 <br>
   - 코드:
```java
@GetMapping("mypage")
public ModelAndView mypage(ModelAndView mv, HttpSession session) {
		User user = userService.getUser((String)session.getAttribute("userId"));
		mv.addObject("user", user);
		mv.setViewName("user/mypage");
		return mv;
}
```
   - 설명: 정보 조회, 계정 관리, 로그아웃, 회원탈퇴 등의 기능 제공 <br>
   - 개선점 1. 간소화 가능 -> 반환 타입 String으로 개선 가능 <br>
    　　　　　　　　　 -> 모델에 직접 데이터 추가, 뷰 이름 반환으로 코드 간결화 가능 <br>
```java
@GetMapping("mypage")
public String mypage(Model model, HttpSession session) {
    User user = userService.getUser((String) session.getAttribute("userId"));
    model.addAttribute("user", user);
    return "user/mypage";
}
```

>> **회원수정**
   - 수정할 데이터 입력 -> 유효성 검사 -> 회원 정보 수정 <br>
   - 코드:
```java
@PutMapping("fixUser")
public int fixUser(@RequestBody UserGenre userGenre) {
		userService.delUserGenre(userGenre.getUser().getUserNum());
		userService.fixUser(userGenre.getUser());
		List<Integer> genres = userGenre.getGenreNum();
		for(int genre: genres) {
			userService.addUserGenre(userGenre.getUser().getUserNum(), genre);
		}
		return userService.fixUser(userGenre.getUser());
}
```
   - 설명: 사용자가 원하는 내용으로 데이터 수정 <br>
   - 개선점 1. 데이터 일관성 유지 -> 트랜젝션으로 개선 가능 <br>
    　　　2. 비동기 처리 고려 -> 응답 시간 향상 가능 But 코드 복잡성 증가, 가독성 저하 가능성 있음 <br> 　　　3. Soft Delete 고려 -> 데이터 보존, 복구 가능 But 데이터 크기 증가, 쿼리 복잡성 증가 <br>

>> **회원탈퇴**
   - 회원 탈퇴 -> 회원 탈퇴 ID Number 저장 <br>
   - 코드:
```java
@PostMapping("addWithDrawal")
public void addWithDrawal(@RequestBody User userNum, HttpSession session) {
		userService.addWithDrawal(userNum.getUserNum());
		session.invalidate();
}
```
   - 설명: 회원 탈퇴 테이블에 탈퇴한 ID 보관  <br>
   - 개선점 1. 명확성 및 확장성 고려 -> DTO 클래스로 개선 가능 <br>
   　　　2. 탈퇴 아이디 정보 고려 -> 토큰, 세션 등을 활용하여 탈퇴 정보 없이 관리 <br>

>## 프로젝트 개선 방향
>> **보안강화**
   - Spring Security를 사용하거나 해시 함수 구현 <br>
   - HTTPS 사용

>> **JWT 도입**
   - 효율적으로 세션 관리 <br>

>> **클라이언트 통신 최적화**
   - AJAX나 비동기 처리로 응답 속도 향상

>> **코드 리팩토링 및 구조화**
   - 비지니스 로직과 트랜잭션 관리를 서비스 계층으로 분리하여 확장성, 간결성 증가 <br>