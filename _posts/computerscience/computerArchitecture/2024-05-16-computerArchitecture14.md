---
title: "트랜지스터, CPU"
date: 2024-05-16 10:00:00 PM +09:00
categories: [ComputerScience, ComputerArchitecture]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>트랜지스터</span>
- 단자 한쪽에 전류를 흘리면 나머지 단자 두 개에 전류가 흐르게 할 수도 있고 흐르지 못하게 할 수도 있다. <br>
- 본질은 스위치와 동일하다. <br>
- 프로그래머가 작성한 프로그램이 아무리 복잡해도 소프트웨어가 수행하는 기능은 최종적으로 이 작은 물건의 간단한 개폐 작업으로 완성된다. <br>

>## <span style='color:#1E90FF'>논리곱, 논리합, 논리부정</span>
- 트랜지스터로 다음 세 가지 회로를 만들 수 있다.
    - 스위치 두 개가 동시에 켜질 때만 전류가 흐르고 등이 켜진다.
    - 두 스위치 중 하나라도 켜져 있으면 전류가 흐를 수 있으며 등이 켜진다.
    - 스위치를 닫으면 전류가 흘러 등이 켜지지만, 스위치를 열면 전류가 흐르지 않고 등이 꺼진다.
- 위 세 가지 회로를 각각 논리곱 게이트, 논리합 게이트, 논리부정 게이트 라고 한다. <br>
- 위 세 가지 회로로 모든 논리 함수를 표현할 수 있다. <br>
- 이것을 논리적 완전성이라고 한다. <br>

>## <span style='color:#1E90FF'>CPU의 연산 능력</span>
- 덧셈으로 예를 들어보자.
    - 0 + 0 = 결과 : 0, 자리 올림수 : 0
    - 0 + 1 = 결과 : 1, 자리 올림수 : 0
    - 1 + 0 = 결과 : 1, 자리 올림수 : 0
    - 1 + 1 = 결과 : 0, 자리 올림수 : 1
- 두 입력 값 두개가 모두 1일 때만 자리 올림수가 1이다. 논리곱 게이트다. <br>
- 두 입력 값이 서로 다르면 결과가 1이고, 두 입력 값이 서로 같으면 결과가 0이다. 이것을 배타적 논리합이라고 한다.
- 논리곱 게이트와 배타적 논리합 게이트 한 개를 조합하면 2진법 덧셈을 구현할 수 있다. <br>
- 이것이 바로 가산기(adder)이다. <br>
- 덧셈 외에도 요구 사항에 따라 다른 산술 연산도 설계할 수 있다. CPU에는 전문적으로 계산을 담당하는 모듈이 있는데, 이것을 바로 산술 논리 장치, ALU라고 한다. <br>
- 회로는 연산 능력 뿐만아니라 정보를 기억할 수 있어야 한다. <br>

>## <span style='color:#1E90FF'>레지스터와 메모리</span>
- 전원이 연결되어 있는 한 정보를 저장할 수 있지만, 전원이 끊기면 저장된 정보는 모두 사라진다. <br>

>## <span style='color:#1E90FF'>클럭</span>
- 회로는 많은 부분으로 구성되어 있는데, 일부는 데이터를 계산하는 데 사용되고 일부는 정보를 저장하는 데 사용된다. <br>
- 각 부분의 회로가 함께 작업할 수 있도록, 조정하거나 동기화 하려면 클럭 신호가 필요하다. <br>
- 클럭 신호가 전압을 변경할 때 마다 전체 회로의 각 레지스터, 즉 전체 회로 상태가 갱신된다. <br>
- CPU의 클럭 주파수는 1초 동안 얼마나 흔드는지를 의미하며, 클럭 주파수가 높을수록 CPU가 1초에 더 많은 작업을 할 수 있다. <br>

>## <span style='color:#1E90FF'>CPU</span>
- 각종 계산이 가능한 산술 논리 장치, 정보를 저장할 수 있는 레지스터, 작업을 함께하도록 제어해 주는 클럭 신호를 갖추었고, 이를 한데 묶은 것을 중앙 처리 장치, CPU 또는 프로세서 라고 한다. <br>