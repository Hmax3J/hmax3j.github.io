---
title: "JAVA Method 호출과 반환"
date: 2024-02-25 6:00:00 PM +09:00
categories: [JAVA, Syntax_Method]
tags: [java, syntax, method]
---
***

>## <span style='color:#1E90FF'>기록하자.</span>
Method에 대해 공부하면서 중요하다고 생각이 들어 까먹지 않게 메모하고 싶어 글을 남긴다. <br>

>## <span style='color:#1E90FF'>JAVA에서 함수는 Method</span>
JAVA에서는 함수를 Method라고 한다. <br>
Method는 코드의 재사용성을 높이고 프로그램을 모듈화하여 유지보수성을 개선하는 데 도움이 된다. <br>

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```
> 위 코드는 Method를 정의한 것이다. Method는 선언과 본문으로 나눌 수 있다. <br>
public static int add(int a, int b) 는 Method 선언 부분이다. <br>
접근 제어, 반환 타입, Method 이름, 파라미터(매개변수)를 포함한다. <br>
int a, int b 부분이 파라미터이다. 여기에 들어가는 값을 Argument(아규먼트), 인수, 인자라 부른다. <br>
즉, int a에 10, int b에 20이 들어갔으면 10, 20이 아규먼트, 인수, 인자라고 한다. <br>
위 Method처럼 반환 타입이 있는 경우 반드시 return으로 값을 반환해야 한다. <br>
Method는 반환 타입이 없거나 매개변수가 없는 경우도 있다. <br>
반환 타입이 없는 경우 return을 생략할 수 있다. JAVA가 자동으로 return을 넣어준다. <br>
return을 만나면 해당 Method는 종료된다. <br>

>## <span style='color:#1E90FF'>JAVA는 변수의 값을 복사한다.</span>
JAVA는 변수의 값을 항상 복사한다. 이것이 무슨 뜻인지 알아보자. <br>

```java
int a = 5;
int b = a;
b = 10;
```
> 위 코드와 같이 선언을 했다면 결과는 어떻게 나올까? <br>
출력문으로 확인하면 a = 5, b = 10으로 나오게 된다. <br>
int b에 a 값을 복사했지만 바로 밑에서 b에 다시 10을 대입했기 때문에 값이 재할당 된다. <br>
복사했다는 뜻의 의미는 b = a 부분에서 a가 b에 들어가는 것이 아니라 a의 값을 b에 할당한다. <br>
그래서 복사한다. 라고 말한다. <br>
갑자기 이것을 왜 말하는지에 대해 의문이 생길 수 있다. 그것은 Method에서 알아보자.

>## <span style='color:#1E90FF'>Method 호출과 값 복사</span>
이 내용은 영한님 자바 강의를 듣다가, 중요하다 생각이 들어 기록하게 되었다. <br>

```java
public class Method {
    public static void main(String[] args) {
        int number = 5;
        changeNumber(number);
    }

    public static void changeNumber(int number) {
        number = number * 2;
    }
}
```
> 위 코드는 결과 값이 어떻게 나오는가? <br>
혹시 5, 10 이라 생각했다면 JAVA의 특징을 기억하자. <br>
JAVA는 항상 값을 복사해서 대입한다. <br>
그리고 main에서 선언한 number와 Method에서 사용하는 number는 같지 않다. 서로 다른 변수다. <br>
왜 다른 변수인가 ? 바로 변수의 Scope 때문이다. <br>
즉, 같은 블럭안에서만 유효하고, 블럭이 다르면 영향을 주지 못한다. <br>
그래서 결과 값은 5, 10이 나오게 된다. <br>
그렇다면 메소드를 호출해서 main에 있는 변수의 값을 바꾸려면 어떻게 해야하는가? 이제 알아보자. <br>

>## <span style='color:#1E90FF'>Method 값 반환</span>
main에서 변수 값을 Method를 통해 변환하려면 Method의 반환을 활용하면 된다. <br>

```java
public class Method {
    public static void main(String[] args) {
        int number = 5;
        number = changeNumber(number);
    }

    public static int changeNumber(int number) {
        number = number * 2;
        return number;
    }
}
```
> 이렇게 Method에서 return을 활용해 값을 반환한다면 main의 number에는 <br>
number * 2 한 값이 대입된다. 즉 number의 값을 바꿀 수 있다. <br>
이 전에는 Method의 return 값이 void였다. 그래서 아무 것도 반환하지 않아 number의 값이 그대로였다. <br>
이 Method는 int 값을 return 하기 때문에 int 변수인 number에 값을 대입 할 수 있다. <br>
main에서 Method를 활용해 값을 바꾸고 싶으면 Method의 return 값을 활용하면 된다. <br>