---
title: "JAVA DataType, 기본형과 참조형"
date: 2024-02-27 11:00:00 AM +09:00
categories: [Back-End, JAVA]
tags: [java, syntax, datatype, method]
---
***

>## <span style='color:#1E90FF'>기록하자.</span>
JAVA DataType에 대해 공부하면서 중요하다고 생각이 들어 까먹지 않게 메모하고 싶어 글을 남긴다. <br>

>## <span style='color:#1E90FF'>기본형(Primitive Data Types)</span>
- 정수 타입 (Integer Types)
  - `byte`: 8비트 부호 있는 정수
  - `short`: 16비트 부호 있는 정수
  - `int`: 32비트 부호 있는 정수 (기본값)
  - `long`: 64비트 부호 있는 정수
- 실수 타입 (Floating-Point Types)
  - `float`: 32비트 부동 소수점
  - `double`: 64비트 부동 소수점 (기본값)
- 문자 타입 (Character Type)
  - `char`: 16비트 유니코드 문자
- 논리 타입 (Boolean Type)
  - `boolean`: true 또는 false 값만 가짐

>## <span style='color:#1E90FF'>참조형(Reference Data Types)</span>
- 클래스 타입 (Class Types)
  - 사용자가 정의한 클래스들이 여기에 해당합니다.
- 인터페이스 타입 (Interface Types)
  - 사용자가 정의한 인터페이스들이 여기에 속합니다.
- 배열 타입 (Array Types)
  - 배열은 기본형과 참조형 모두를 담을 수 있습니다.
- 기타 타입 (Other Types)
  - 예를 들어, 열거 타입(enum) 등이 여기에 포함됩니다.

>## <span style='color:#1E90FF'>기본형과 참조형</span>
자바에서는 기본형(Primitive Data Types)과 참조형(Reference Data Types) 2가지의 데이터타입을 제공한다. <br>
- 기본형
    - 소문자로 시작한다. int, double, char, boolean 등
    - 단순한 값을 저장하는 데 사용
    - 기본값으로 자동 초기화
    - 값이 복사되므로 한 변수의 값 변경이 다른 변수에 영향을 주지 않는다.
    - 기본형은 고정된 크기를 가지며 스택 메모리에 저장
- 참조형
    - 대문자로 시작한다. String, List, Object, MyClass 등
    - 객체를 가리키는데 사용되며 객체의 주소를 저장
    - 명시적으로 객체를 생성해야 하며, 그렇지 않으면 null로 초기화
    - 주소를 공유하므로 한 객체의 내용을 변경하면 다른 참조도 영향을 받는다.
    - 참조형은 가변적인 크기를 가지며 객체는 힙 메모리에 저장

>## <span style='color:#1E90FF'>Method 호출</span>
Method 호출 할 때 기본형과 참조형의 값 전달의 차이점이 있어 글을 쓰게 되었다. <br>
아래 코드는 기본형을 Method로 호출 할 때의 값 전달이다.

```java
public class PrimitiveExample {
    public static void main(String[] args) {
        int num = 10;
        System.out.println("main num: " + num);
        modifyValue(num);
        System.out.println("modify num: " + num);
    }

    static void modifyValue(int x) {
        x = 20;
    }
}
```
```
main num: 10
modify num: 10
```
> 위의 출력 결과가 기본형을 잘 나타낸다. <br>
즉, 기본형은 메소드에서 값을 변경해도 호출한 곳의 값은 변하지 않는다. <br>
값을 변경 하려면 아래 코드와 같이 해당 Method의 반환값을 활용하여 변경된 값을 다시 할당해야 한다.

```java
public class PrimitiveExample {
    public static void main(String[] args) {
        int num = 10;
        System.out.println("main num: " + num);
        num = modifyValue(num);
        System.out.println("modify num: " + num);
    }

    static int modifyValue(int x) {
        x = 20;
        return x;
    }
}
```

> 아래 코드는 참조형을 Method로 호출 할 때의 값 전달이다.

```java
public class ReferenceExample {
    public static void main(String[] args) {
        ReferenceData rData = new ReferenceData();
        rData.value = 10;
        System.out.println("main rData = " + rData.value);
        modifyValue(rData);
        System.out.println("modify rData = " + rData.value);
    }

    public static void modifyValue(ReferenceData reData) {
        reData.value = 20;
    }
}

public class ReferenceData {
    int value;
}
```
```
main rData: 10
modify rData: 20
```
> Method에서 매개변수로 받은 reData는 rData와 같은 주소를 참조한다. <br>
그래서 Method에서 reData의 값을 변경하면 rData와 같은 주소를 참조하기 때문에 rData의 값도 변경된다. <br>
기본형과 참조형의 차이는 이와 같다. <br>
기본형은 Method에서 값을 변경해도 호출 값이 변하지 않는다. <br>
기본형을 Method로 값을 변경하려면 반환값을 받아 재할당 해야 한다. <br>
참조형은 같은 객체를 참조할 때 Method에서 값을 변경한다면 호출 값이 변경된다.