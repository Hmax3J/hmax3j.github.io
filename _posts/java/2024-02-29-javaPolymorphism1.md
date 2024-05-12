---
title: "JAVA OOP, 다형적 참조"
date: 2024-02-29 10:00:00 PM +09:00
categories: [JAVA, OOP_Polymorphism]
tags: [java, oop, polymorphism, extends]
---
***

>## <span style='color:#1E90FF'>기록하자.</span>
JAVA OOP에 대해 공부하면서 중요하다고 생각이 들어 까먹지 않게 메모하고 싶어 글을 남긴다. <br>

>## <span style='color:#1E90FF'>OOP(Object-Oriented Programming)</span>
OOP(Object-Oriented Programming)는 객체를 기반으로 프로그램을 설계하는 프로그래밍 패러다임이다. <br>
그 중 다형성(Polymorphism)은 OOP의 핵심 개념 중 하나다. <br>
그래서 다형성(Polymorphism)에 대해 공부하고 기록하여 머리에 남겨두려고 한다. <br>
다형성(Polymorphism)에 대해 알아보자.

>## <span style='color:#1E90FF'>다형성(Polymorphism)</span>
다형성의 개념은 바로 하나의 객체가 여러 가지 형태로 작동하거나 여러 가지 의미를 가질 수 있는 능력이다. <br>
다형성은 크게 다형적 참조, 메서드 오버라이딩에 대해 알아야 한다. 먼저, 다형적 참조에 대해 알아보자. <br>

>## <span style='color:#1E90FF'>다형적 참조</span>
```java
public static void main(String[] args) {
        Parent parent = new Parent();
        Child child = new Child();
        Parent poly1 = new Child();
        Parent poly2 = child;
        Child poly3 = new Parent();
        Child poly4 = parent;
}
```
위 코드가 있을 때 2,3,4,5 라인처럼 선언을 할 경우 업캐스팅이 일어나 서브 클래스에 참조할 수 있다. <br>
이것을 다형적 참조라고 한다. <br>
다형적 참조는 상위 클래스 타입의 참조 변수가 서브 클래스 객체를 참조할 수 있는 기능이다. <br>
하지만 여기서 서브 클래스 객체의 기능은 사용하지 못한다. <br>
서브 클래스 객체의 기능을 사용하려면 다운캐스팅이 필요하다. <br>
다운캐스팅이란 상위 클래스 타입의 참조 변수를 서브 클래스 타입으로 변환하는 것을 의미한다. <br>
업캐스팅은 생략이 가능하지만 다운캐스팅은 명시해야 한다. <br>
하지만 다운캐스팅은 조심해서 사용을 해야 한다. 심각한 런타임에러가 발생할 수 있기 때문이다. <br>

>## <span style='color:#1E90FF'>ClassCastException</span>
다운캐스팅을 했을 때 ClassCastException 런타임 에러가 발생 할 수 있다. 왜 발생하는지 알아보자.
```java
public static void main(String[] args) {
        Parent parent1 = new Parent();
        Child child1 = (Child) parent1;
        child1.method();
        ----------------------------------
        Parent parent2 = new Child();
        Child child2 = (Child) parent2;
        child2.method();
}
```
위 코드가 있을 때 위, 아래 실행 결과가 어떻게 나올지 예상이 되는가 ? <br>
예상이 가는 방문자는 다형적 참조에 대해 이해를 하고 있을 확률이 높다. <br>
결과는 위의 코드는 런타임에러가 발생하고 아래 코드는 정상적으로 진행된다. <br>
하지만 여기서는 위 코드가 런타임 에러라 아래 코드의 결과가 나오지 않으니 유의하자. <br>
왜 런타임 에러가 나오는지 알아보자. <br>
먼저 위의 코드는 parent1에 상위 클래스인 Parent를 참조했다. <br>
여기서 중요한 것은 상위 클래스로 참조할 때 서브 클래스는 참조하지 못한다는 것이다. <br>
그 이유는 컴파일 시점에 클래스 정보만 확인하기 때문이다. <br>
다시 말하면, 객체 생성 시점에는 서브 클래스 객체가 생성될 수 있지만, <br>
컴파일 시점에는 서브 클래스가 존재하는지 여부를 알 수 없다. <br>
그래서 상위 클래스를 참조할 경우 서브 클래스를 알 수 없는 것이다. <br>
이것을 해결하기 위해 참조할 때 위의 6번 라인처럼 서브 클래스를 참조해야 하는 것이다. <br>
서브 클래스를 참조하게 되면 서브 클래스는 객체가 생성 될 때 상속을 한 상위 클래스 전부, <br>
메모리에 생성하기 때문이다. 즉 서브 클래스가 생성 될 때 서브 클래스 안에는 <br>
상위 클래스, 서브 클래스 이렇게 생성이 된다. 그래서 상위 클래스, 서브 클래스 전부 참조 할 수 있다. <br>
위와 같은 상황 때문에 chidl2.method가 실행이 된다. <br>
이렇게 다형성 참조에 대해 알아보았다. OOP에서 아주 중요한 개념이라 제대로 알고 넘어가도록 하자. <br>
다음에는 메소드 오버라이딩에 대해 알아보도록 하자. <br>