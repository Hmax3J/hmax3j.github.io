---
title: "[강의 정리] 3장 - 스택"
date: 2024-09-02 08:30:00 PM +09:00
categories: [ComputerScience, 자료구조]
tags: [cs, computer, science, data, structure]
---
***

>## <span style='color:#1E90FF'>강의 정리</span>
방통대 자료구조 강의를 듣고 내용을 정리하며 복습을 한다. <br>

>## <span style='color:#1E90FF'>스택</span>
- 객체와 그 객체가 저장되는 순서를 기억하는 방법
    - 가장 먼저 입력된 자료가 가장 나중에 출력되는 관계를 표현함
    - 관계를 표현하기 위해서 연산이 필요하다.
    - 객체에 대한 정의와 연산이 모여서 순서가 기억되는 스택의 추상 자료형이 완성된다.
- 0개 이상의 원소를 갖는 유한 순서 리스트
- push와 pop 연산이 한 곳에서 발생하는 자료구조

>## <span style='color:#1E90FF'>스택의 추상 자료형</span>
- CreateStack 연산
    - stack ∈ Stack, item ∈ element, maxStackSize ∈ positive integer
    - ∈은 오른쪽 집합에 왼쪽 원소가 있고, 왼쪽 원소가 오른쪽 집합에 속한다는 뜻이다.
    - stack, item, maxStackSize에 대하여 아래와 같은 연산이 정의된다.
    - stack은 0개 이상의 원소를 갖는 스택
    - item은 스택에 삽입되는 원소
    - maxStackSize는 스택의 최대 크기를 정의하는 정수
    - Stack CreateStack(maxStackSize)
    - 스택의 크기가 maxStackSize인 빈 스택을 생성하고 반환한다.
- Push 연산
    - ```
        Stack Push(stack, item)
            if (StackIsFull(stack))
                then { 'stackFull' 출력 }
                else { 스택의 가장 위에 item 삽입, 스택 반환 }
    ```
    - 중간이나 밑에 삽입할 수 없다.
    - 스택 제일 위에 원소를 삽입한다.
- Pop 연산
    - ```
        Element Pop(stack)
            if (StackIsEmpty(stack))
                then { 'stackEmpty' 출력 }
                else { 스택의 가장 위에 있는 원소를 삭제하고 반환한다. }
    ```
    - 제일 최근에 삽입된, 즉 제일 위에 있는 원소를 삭제한다.
- StackIsFull 연산
    - ```
        Boolean StackIsFull(stack, maxStackSize)
            if (stack의 elements의 개수 == maxStackSize)
                then { 'TRUE' 값을 반환한다. }
                else { 'FALSE' 값을 반환한다. }
    ```
    - 스택 안에 원소가 꽉 차있는지 확인한다.
- StackIsEmpty 연산
    - ```
        Boolean StackIsEmpty(stack)
            if (stack == CreateStack(maxStackSize))
                then { 'TRUE' 값을 반환한다. }
                else { 'FALSE' 값을 반환한다. }
    ```
    - 스택 안에 원소가 비어 있는지 확인한다.

>## <span style='color:#1E90FF'>스택의 응용</span>
- 변수에 대한 메모리의 할당과 수집을 위한 시스템 스택
    - 시스템 스택 : 변수에 대한 메모리의 할당과 수집을 위해 운영체제가 관리하는 스택
- 서브루틴 호출 관리를 위한 스택
- 연산자들 간의 우선 순위에 의해 계산 순서가 결정되는 수식 계산
- 인터럽트의 처리와 되돌아갈 명령 수행 지점을 저장하기 위한 스택
- 컴파일러, 순환 호출 관리

>## <span style='color:#1E90FF'>스택의 연산</span>
- 스택의 삭제 연산
    - 연산자의 위치에 따라 연산의 적용 순서가 달라질 수 있다.
- 스택의 삽입 연산
- 스택의 생성

>## <span style='color:#1E90FF'>사칙연산의 전위, 후위, 중위 표현</span>
- 수식의 계산
    - 연산자의 계산 우선 순위를 생각해야 한다.
    - A + B * C + D
    - ((A + (B * C)) + D)
- 중위 표기법(infix notation)
    - 연산자를 피연산자 사이에 표기하는 방법
    - A + B
    - 사람이 쓴다.
- 전위 표기법(prefix notation)
    - 연산자를 피연산자 앞에 표기하는 방법
    - +AB
- 후위 표기법(postfix notation)
    - 연산자를 피연산자의 뒤에 표기하는 방법
    - AB+
- 중위 표기식의 후위 표기식 변환 방법
    - 먼저 중위 표기식을 연산자의 우선순위를 고려한다.
    - (피연산자, 연산자, 피연산자)의 형태로 괄호로 묶는다.
    - 각 항을 묶고 있는 괄호 안에서 연산자를 항의 가장 오른쪽으로 이동 시킨다.
    - 각 항을 하나의 피연산자로 고려하여 위 과정을 반복한다.
    - 괄호를 모두 제거한다.
- 중위 -> 후위
    - ( A - ( ( B + K ) / D ) )
    - ( A - ( ( BK+ ) / D ) )
    - ( A - ( ( BK+ ) D / ) )
    - A ( ( BK+ ) D / ) -
    - ABK+D/-