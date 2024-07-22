---
title: "[코딩테스트 합격자 되기 스터디] 2주차 - 스택과 큐 (7.14 ~ 7.20)"
date: 2024-07-20 09:35:00 AM +09:00
categories: [Algorithm, Study]
tags: [java, algorithm, study]
---
***

>## <span style='color:#1E90FF'>코딩테스트 합격자 되기 스터디 2주차</span>
강의 보기 -> 해당되는 부분 책 다시 읽기 -> 블로그 정리 <br>
강의는 C++로 되어 있지만 개념적인 내용이라 언어 상관 없이 보고 코드는 각 언어에 맞게 바꾸면 된다. <br>

>## <span style='color:#1E90FF'>참고 강의 및 책</span>
인프런 : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 인프런 강의 링크</a> <br>
Youtube : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 Youtube 링크</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000210881884' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213087020' target='_blank' style='color:red'>코딩테스트 합격자 되기 C++ 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213641007' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바스크립트 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000212576322' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바 편</a> <br>

>## <span style='color:#1E90FF'>ADT란?</span>
- ADT(Abstract Data Type) : 추상 데이터 타입의 약어 <br>
- 세부 사항을 숨기고 사용자에게 필요한 기능만 명시 <br>
- 필요한 연산만 정의함으로써 자료구조 동작 자체에 집중할 수 있다. <br>
- 전화번호부
    - put(name, phone)
    - get(name)
    - remove(name)
    - contains(name)
    - size()
    - 위 기능들같이 필요한 기능만 사용할 수 있다.

>## <span style='color:#1E90FF'>스택의 개념</span>
- LIFO(Last In First Out) : 가장 최근에 들어간 원소가 가장 먼저 출력된다. <br>
- FILO(First In Last Out) : 가장 먼저 들어간 원소가 마지막에 출력된다. <br>
- 가장 최근에 들어온 원소를 알 수 있다. <br>
- 가장 최근에 들어온 원소순으로 출력된다. <br>

>## <span style='color:#1E90FF'>스택의 ADT</span>
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/StackADT.JPG) <br>

>## <span style='color:#1E90FF'>스택의 예시코드</span>
- C++ -> JAVA
```java
import java.util.Stack;
public class Main {
    public static void main(String[] args) {
        Stack<Integer> s = new Stack<>();
        s.push(1); // 스택 s에 데이터 1 추가, 시간 복잡도: O(1)
        s.push(2);
        s.push(3);
        System.out.println(s.peek()); // peek(), 스택의 맨 위 원소 확인, 시간 복잡도: O(1)
        s.pop(); // 스택의 맨 위 원소 제거, 스택이 비어 있으면 예외 발생, 시간 복잡도: O(1)
        System.out.println("Top element after pop: " + s.peek());
        if (!s.isEmpty()) { // 스택이 비어있는지 확인, 시간 복잡도: O(1)
            System.out.println("Stack is not empty");
        } // !연산이 있기 때문에 스택에 데이터가 있을 때 출력문 실행
        System.out.println("Stack size: " + s.size()); // 스택의 크기 확인, 시간 복잡도: O(1)
        while (!s.isEmpty()) {
            System.out.println("Popping element: " + s.peek());
            s.pop(); // 스택데이터를 모두 제거할 때 까지 실행, 시간복잡도: O(1)
        }
        if (s.isEmpty()) {
            System.out.println("Stack is empty after popping all elements");
        }
    }
}
```

>## <span style='color:#1E90FF'>스택의 사용예시1</span>
- 함수 호출
```
void A() {
    System.out.println("Start A");
    B(); 3번
    System.out.println("End A"); 4번
}
void B() {
    System.out.println("Start B");
    System.out.println("End B");
}
int main() { 1번
    A(); 2번
    return 0; 5번
}
```
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/StackUseEx1.JPG) <br>
- 함수 호출 시, 현재 함수의 실행상태를 저장, 새로운 함수로 제어 이동 <br>

>## <span style='color:#1E90FF'>스택의 사용예시2</span>
- 이전 페이지로 가기 <br>
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/StackUseEx2.JPG) <br>
- 페이지 전환할 때 스택에 푸쉬, 이전 페이지로 돌아갈 때 팝 <br>

>## <span style='color:#1E90FF'>스택의 사용예시3</span>
- 괄호 짝 맞추기 <br>
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/StackUseEx3.JPG) <br>
- 열린 괄호 스택에 푸쉬, 닫힌 괄호 나오면 스택에 있는 열린 괄호 팝, 두 개 비교 <br>
- 서로 상쇄되면 계속 진행, 안되면 반복 종료 <br>
- 문자열 끝까지 반복한 후 스택이 비어있으면 성공, 데이터가 있으면 실패 <br>

>## <span style='color:#1E90FF'>큐의 개념</span>
- FIFO(First In First Out) : 가장 먼저 들어간 원소가 가장 먼저 나오는 자료구조 <br>

>## <span style='color:#1E90FF'>큐의 ADT</span>
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/QueueADT.JPG) <br>
- front: 가장 먼저 푸시된 원소의 위치 <br>

>## <span style='color:#1E90FF'>큐의 예시코드</span>
- C++ -> JAVA
```java
import java.util.ArrayDeque;
import java.util.Queue;
public class Main {
    public static void main(String[] args) {
        Queue<Integer> q = new ArrayDeque<>();
        q.offer(1); // offer: 큐의 끝에 요소 추가, 시간복잡도: O(1)
        q.offer(2); // offer 대신 add도 가능하다.
        q.offer(3);
        System.out.println("Front element: " + q.peek()); // peek: 큐의 첫 번째 요소에 접근, O(1)
        q.poll(); // poll: 큐의 첫 번째 요소 제거, O(1)
        System.out.println("Front element after poll: " + q.peek());
        if (!q.isEmpty()) {
            System.out.println("Queue is not empty");
        }
        System.out.println("Queue size: " + q.size()); // size: 큐의 크기 확인, O(1)
    }
}
```

>## <span style='color:#1E90FF'>큐의 사용예시1</span>
- 줄 서기
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/QueueUseEx1.jpg) <br>
    - <a href="https://kr.freepik.com/free-vector/people-in-line-waiting-to-pay_4832282.htm#query=%EC%A4%84%EC%84%9C%EB%8A%94%20%EC%82%AC%EB%9E%8C%EB%93%A4&position=14&from_view=keyword&track=ais_user&uuid=601f8de4-abb6-4271-8313-46a0c79a4da3">작가 pikisuperstar</a> 출처 Freepik <br>
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/QueueUseEx1-2.jpg) <br>
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/QueueUseEx1-3.jpg) <br>
- 제일 앞에 줄 서있는 사람부터 계산을 하고 나간다. <br>

>## <span style='color:#1E90FF'>큐의 사용예시2</span>
- 요세푸스 문제
    - N명의 사람들이 원형으로 둘러앉고, 1~N으로 번호를 매긴다.
    - 시작 위치부터 K번째 사람 제거
    - 제거한 위치부터 다시 K번째 사람 제거
    - 3번째 과정을 한 명이 남을 때 까지 반복
- ![algorithm-study](/assets/img/postImg/algorithm/study/2Week/QueueUseEx2.jpg) <br>
```java
import java.util.ArrayDeque;
import java.util.Queue;
public class Main {
    public static int josephus(int N, int K) {
        Queue<Integer> q = new ArrayDeque<>();
        for (int i = 1; i <= N; i++) { // 큐를 초기화하고 1부터 N까지의 요소를 삽입합니다.
            q.add(i); // 시간복잡도: O(N)
        }
        while (q.size() > 1) { // 큐의 크기가 1이 될 때까지 반복합니다.
            // 첫 번째 K-1개의 요소를 큐의 뒤로 이동시킵니다.
            for (int i = 0; i < K - 1; i++) {
                q.add(q.poll()); // 시간복잡도: O(N * K)
            }
            q.poll(); // K번째 요소를 제거합니다.
        }
        return q.peek();
    }
    public static void main(String[] args) {
        int N = 5; // 예시: 5명의 사람이 있을 때
        int K = 2; // 예시: 매 2번째 사람을 제거할 때
        System.out.println("The survivor is: " + josephus(N, K));
    }
}
```

>## <span style='color:#1E90FF'>정리</span>
- 스택(Stack)
    - LIFO
    - 함수 호출 관리
    - 페이지 탐색
    - 괄호 짝 맞추기
    - 가장 최근 원소를 봐야하는 경우에 사용
    - DFS, 백트래킹에서 사용
- 큐(Queue)
    - FIFO
    - 줄 서기
    - 요세푸스
    - 들어온 순서대로 나갈 때 사용
    - BFS에서 사용

>## <span style='color:#1E90FF'>괄호 회전하기 문제 풀이</span>
- <a href='https://school.programmers.co.kr/learn/courses/30/lessons/76502' target='_blank' style='color:red'>괄호 회전하기</a> <br>