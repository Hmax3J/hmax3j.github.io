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
```
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
   - 개선점 1. 비밀번호 해시처리 필요, Spring Security || 해시 함수 구현을 통해 개선 가능 <br>
   　　　2. 토큰 기반의 인증 방식 도입시 세션보다 더욱 단순하게 관리 가능, JWT 활용으로 개선 가능 <br>
   　　　3. 응답 형식 표준화 필요, ResponseEntity로 상태 코드와 메시지를 명시적으로 반환으로 개선 가능 <br>
   　　　4. HTTPS 사용 고려, 이유는 ? 데이터 암호화로 데이터 변조나 도청을 방지, SEO 이점 <br>

>> **로그아웃**
   - 로그아웃 -> 세션 종료, 로그인 상태 해제 -> 리다이렉트 <br>
   - 코드:
```
@GetMapping("/logout")
public ModelAndView logout(ModelAndView mv, HttpSession session) {
    session.invalidate();
    mv.setViewName("redirect:/");
	return mv;
}
```
   - 설명: REST API 사용 <br>
   - 개선점 1. GET은 보안에 취약, POST 메서드 사용으로 개선 가능 <br>
   　　　2. 간소화 가능, 반환 타입 String으로 개선 가능 <br>
```
@PostMapping("/logout")
public String logout(HttpSession session) {
    session.invalidate();
    return "redirect:/";
}
```

>> **회원가입**
   - 추후 작성 <br>
   - 코드: