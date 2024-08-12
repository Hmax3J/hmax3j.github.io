---
title: "[스프링 부트 3 백엔드 개발자 되기 - 자바 편(2판) 스터디] - 2주차 (8.5 ~ 8.11)"
date: 2024-08-10 01:00:00 AM +09:00
categories: [bookStudy, 스프링부트3 백엔드 개발자 되기 - 자바 (2판)]
tags: [java, study, spring, boot]
---
***

>## <span style='color:#1E90FF'>스프링 부트 3 백엔드 개발자 되기 - 자바 편(2판) 스터디 2주차 </span>
책을 읽고 공부한 내용을 정리하기

>## <span style='color:#1E90FF'>책</span>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000201766024' target='_blank' style='color:red'>스프링 부트 3 백엔드 개발자 되기 - 자바 편(2판)</a> <br>

>## <span style='color:#1E90FF'>엔터프라이즈 애플리케이션</span>
대규모의 복잡한 데이터를 관리하는 애플리케이션을 말한다. <br>
몇 백만, 몇 천만의 사용자가 한 번에 잔고 조회, 입금, 출금, 통장 개설을 하기도 한다. <br>
이렇듯 엔터프라이즈 애플리케이션은 많은 사용자의 요청을 동시에 처리해야 하므로 <br>
서버 성능, 안정성, 보안이 매우 중요하다. <br>
이런 점들을 해결할 수 있는 것이 바로 <span style='color:red'>스프링</span>이다. <br>

>## <span style='color:#1E90FF'>스프링</span>
스프링은 프레임워크다. 서버 성능, 안정성, 보안을 매우 높은 수준으로 제공한다. <br>
스프링 프레임워크의 주요 개념과 특징은 다음과 같다. <br>
● <span style='color:red'>의존성 주입</span>(Dependency Injection, DI) <br>
● <span style='color:red'>제어의 역전</span>(Inversion of Control, IoC) <br>
● <span style='color:red'>AOP</span>(Aspect-Oriented Programming) <br>
● <span style='color:red'>모듈성</span> <br>
더 많은 개념과 특징이 있지만 너무 방대하기 때문에 이 정도만 작성했다. <br>

>## <span style='color:#1E90FF'>스프링 부트</span>
스프링은 설정이 매우 복잡하다. 이런 복잡함을 해결하기 위해 스프링 부트가 생겼다. <br>
빠르게 스프링 프로젝트를 설정할 수 있고 스타터를 사용해 간편하게 의존성을 사용하거나 관리할 수 있다. <br>
WAS(웹 어플리케이션 서버)가 내장되어 있어 따로 설치하지 않아도 된다. <br>
스프링 부트는 스프링과 다른 것이 아니고 스프링에 속한 도구이다. <br>
 ----스프링----- <br>
│　　　　　　　　│ <br>
│　스프링 부트　│ <br>
│　　　　　　　　│ <br>
 --------------- <br>
이런 느낌이다. <br>
스프링은 엔터프라이즈 애플리케이션 개발을 더 쉽게 만드는 도구이고 <br>
스프링 부트는 스프링의 개발을 더 빠르고 쉽게 하기 위해 사용하는 도구다. <br>

>## <span style='color:#1E90FF'>IoC</span>
IoC는 Inversion of Control의 줄임말이다. 제어의 역전이라는 뜻이다. <br>
```java
public class B {
    // B 클래스의 내용
}
public class A {
    private B b;
    // 생성자를 통한 의존성 주입 (생성자 주입 방식)
    public A(B b) {
        this.b = b;
    }
}
```
원래는 위 코드 처럼 직접 객체를 생성했다. 이 경우, A 클래스는 B 클래스에 강하게 결합되어 있으며, <br>
A 클래스가 B 객체를 생성하는 책임을 가지고 있다. 이는 클래스 간의 의존성이 높아지는 문제가 생긴다. <br>
제어의 역전(IoC)은 이 책임을 개발자가 아닌 외부의 프레임워크(스프링)가 맡도록 하여, <br>
객체의 생성과 제어를 프레임워크가 담당한다. <br>
개발자는 객체의 생성 방식을 신경 쓰지 않고, 프레임워크가 제공하는 흐름을 따르기만 하면 된다. <br>
이로 인해 객체의 생성, 초기화, 소멸 등의 제어가 <span style='color:red'>"역전"</span>된 것이다. <br>
```java
@Component
public class B {
    // B 클래스의 내용
}
@Component
public class A {
    private B b;
    // 생성자를 통한 의존성 주입
    @Autowired
    public A(B b) {
        this.b = b;
    }
}
```
이 방식에서는 A 클래스가 B 객체를 직접 생성하지 않고, 외부에서 생성된 B 객체를 주입받는다. <br>
스프링 프레임워크가 B 객체를 생성하여 A 클래스에 주입한다. <br>
이로 인해 A 클래스는 B 클래스에 덜 결합되고, 더 유연한 구조를 가지게 된다. <br>
요약하자면 제어의 역전이란 단순히 객체 생성만이 아니라, <br>
객체의 라이프사이클 전체(생성, 초기화, 소멸 등)를 프레임워크가 관리한다는 뜻이다. <br><br>
@Component <br>
클래스에 붙여서 스프링 컨테이너가 해당 클래스를 빈으로 관리하도록 한다. <br>
객체의 생성과 관리가 스프링 컨테이너에 의해 자동으로 이루어진다. <br><br>
@Autowired <br>
빈(Bean)의 의존성을 자동으로 주입받기 위해 사용된다. <br>
@Autowired를 사용하면, 스프링이 빈을 자동으로 주입해준다. <br>

>## <span style='color:#1E90FF'>DI</span>
DI는 Dependency Injection의 줄임말이다. 의존성 주입이라는 뜻이다. <br>
제어의 역전을 구현하기 위해 사용하는 방법이다. <br>
DI는 어떤 클래스가 다른 클래스에 의존한다는 뜻이다. <br>
다르게 말하면 한 객체가 다른 객체를 필요로 할 때, 그 객체를 의존한다고 말한다. <br>
예를 들어, Car 클래스가 Engine 객체를 필요로 한다면, Car는 Engine에 의존하고 있는 것이다. <br>
```java
public class Car {
    private Engine engine;
    public Car() {
        this.engine = new Engine();  // 직접 생성
    }
}
```
여기서 Car 클래스는 Engine 객체를 직접 생성하고 관리한다. <br>
이 방식의 문제점은 Car가 Engine 객체의 생성과 관리에 직접 관여해야 한다는 점이다. <br>
DI의 주요 방식은 3가지가 있다. <br><br>
● <span style='color:red'>생성자 주입</span> (Constructor Injection) <br>
```java
public class Car {
    private Engine engine;
    // 생성자를 통한 의존성 주입
    public Car(Engine engine) {
        this.engine = engine;
    }
}
```
의존성을 생성자의 매개변수로 주입받는 방식이다. <br>
Car 클래스는 Engine 객체를 생성자 매개변수로 받아서 의존성을 주입받는다. <br>
이 방식은 주입받는 의존성이 final로 설정되므로 불변성을 보장한다. <br><br>
● <span style='color:red'>필드 주입</span> (Field Injection) <br>
```java
public class Car {
    @Autowired
    private Engine engine;  // @Autowired 어노테이션 사용
    // 생성자나 메서드 없이 자동 주입
}
```
의존성을 클래스의 필드에 직접 주입받는 방식이다. <br>
@Autowired 어노테이션을 사용하여 스프링 프레임워크가 자동으로 의존성을 주입한다. <br><br>
● <span style='color:red'>메서드 주입</span> (Method Injection) <br>
```java
public class Car {
    private Engine engine;
    @Autowired
    public void setEngine(Engine engine) {
        this.engine = engine;
    }
}
```
의존성을 클래스의 메서드에 주입받는 방식이다. <br>
Engine 객체가 setter 메서드를 통해 주입된다. <br>
@Autowired는 스프링 컨테이너에 있는 빈이라는 것을 자동으로 주입받는다. <br>
빈은 스프링 컨테이너에서 관리하는 객체를 말한다. <br>

>## <span style='color:#1E90FF'>스프링 컨테이너</span>
스프링 프레임워크의 핵심 구성 요소로서, 애플리케이션의 객체를 생성하고 관리하며, <br>
의존성 주입을 수행하는 역할을 한다. <br>
즉, 빈이 생성되고 소멸되기까지의 생명주기를 이 스프링 컨테이너가 관리한다. <br>
주요 기능 <br>
● <span style='color:red'>빈(Bean) 생성 및 관리</span> <br>
● <span style='color:red'>의존성 주입</span>(Dependency Injection) <br>
● <span style='color:red'>빈 생명 주기 관리</span> <br>
위 기능이 스프링 컨테이너가 한다고 했지만 스프링 컨테이너 안의 구성 요소인 <br>
애플리케이션 컨텍스트가 위 기능을 수행한다. <br>

>## <span style='color:#1E90FF'>빈</span>
빈은 스프링 컨테이너가 제공하는 것이 아니라, 스프링 컨테이너에 의해 생성되고 관리되는 자바 객체다. <br>
빈의 정의는 XML, 자바 설정, 또는 컴포넌트 스캔을 통해 이루어진다. <br>
클래스가 빈으로 등록되면 빈의 이름은 클래스 이름의 첫 글자를 소문자로 바꾼 이름이다. <br>
예를 들어 MyBean이 클래스 이름이면 빈의 이름은 myBean이다. <br>