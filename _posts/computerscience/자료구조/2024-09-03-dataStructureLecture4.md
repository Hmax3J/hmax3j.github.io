---
title: "[강의 정리] 4장 - 큐"
date: 2024-09-03 03:00:00 AM +09:00
categories: [ComputerScience, 자료구조]
tags: [cs, computer, science, data, structure]
---
***

>## <span style='color:#1E90FF'>강의 정리</span>
방통대 자료구조 강의를 듣고 내용을 정리하며 복습을 한다. <br>

>## <span style='color:#1E90FF'>큐</span>
- 대중교통을 타기 위해 서 있는 행렬
- 병원의 접수대
- 은행의 예금 인출기
- 백화점의 계산대 위에 놓인 상품들
- 작업 큐에 들어간 작업이 가장 처음에 처리되는 작업 스케줄
- 한쪽에서는 삽입연산만 가능하다.
    - 다른 한쪽에서는 삭제연산만 가능하다.
- 선입 선출 (First In First Out, FIFO) 또는 선착순 서브 (First Come First Serve) 알고리즘과 함께 사용됨
- 삭제가 일어나는 곳 : front
- 삽입이 일어나는 곳 : rear

>## <span style='color:#1E90FF'>큐의 추상 자료형</span>
- 큐의 연산
    - queue ∈ Queue, item ∈ element, maxQueueSize ∈ positive integer
    - ∈은 오른쪽 집합에 왼쪽 원소가 있고, 왼쪽 원소가 오른쪽 집합에 속한다는 뜻이다.
    - queue, item, maxQueueSize에 대하여 아래와 같은 연산이 정의된다.
    - queue는 0개 이상의 원소를 갖는 큐
    - item은 큐에 삽입되는 원소
    - maxQueueSize는 큐의 최대 크기
- 큐의 삽입(Add_q) 연산
    - ```
        Queue Add_q(queue, item)
            if (IsFull_q(queue))
                then { 'queueFull'을 출력한다. }
                else { 큐의 rear에서 item을 삽입하고, 큐를 반환한다. }
    ```
- 큐의 삭제(Delete_q) 연산
    - ```
        Element Delete_q(queue)
            if (IsEmpty_q(queue))
                then { 'queueEmpty'를 출력한다. }
                else { 큐의 front에 있는 원소를 삭제하고 반환한다. }
    ```
- 빈 큐 검사(IsEmpty_q) 연산
    - ```
        Boolean IsEmpty_q(queue)
            if (rear == front)
                then { 'TRUE' 값을 반환한다. }
                else { 'FALSE' 값을 반환한다. }
    ```
- 큐 만원 검사(IsFull_q) 연산
    - ```
        Boolean IsFull_q(queue, maxQueueSize)
            if (queue의 elements의 개수 == maxQueueSize)
                then { 'TRUE' 값을 반환한다. }
                else { 'FALSE' 값을 반환한다. }
    ```
- front와 rear가 같은 위치에 있다면 큐가 비어 있다는 것을 알 수 있다.
- front가 2고 rear가 2일때 Add연산을 한다면 rear 3에 데이터가 저장된다.

>## <span style='color:#1E90FF'>큐의 응용</span>
- CPU의 관리 방법(1), FCFS 스케줄링
    - FCFS(First-Come First-Served) 스케줄링(또는 FIFO 스케줄링이라고도 함)
    - 작업(프로그램)이 준비 큐에 도착한 순서대로 CPU를 할당받고 완료될 때까지 CPU를 사용하는 기법
- CPU의 관리 방법(2), RR 스케줄링
    - RR(Round Robin) 스케줄링 기법은 대화형 시스템에 적합하다.
    - 일정 시간(time slice)만 CPU를 사용하는 스케줄링 방식
    - A(30분), B(10분), C(5분)일 때 CPU 사용 시간 제한을 10분으로 두었을 때
    - A(10분) -> B(10분) -> B 완료 -> C(5분) -> C 완료 -> A(10분) -> A(10분) -> A 완료
    - 공평하게 CPU를 배분해서 쓸 수 있는 것이 라운드 로빈 스케줄링이다.
    - CPU의 시간 할당량 또는 시간 간격에 의해 제한을 받는다.
    - 일정한 크기의 시간 할당량을 모든 작업에 준다.
    - 그 시간 동안 작업이 완료되지 못하면 준비 큐의 맨 뒤에 다시 배치된다.

>## <span style='color:#1E90FF'>배열을 이용한 큐의 구현</span>
- 큐의 생성
    - 변수 rear의 초기 값은 큐의 공백 상태를 나타내는 -1로 시작한다.
- 큐의 삽입 연산
    - 삽입 연산이 발생하면 rear 변수만 오른쪽으로 이동한다.
    - 삭제 연산이 발생하면 front 변수만 오른쪽으로 이동한다.
- 큐의 삭제 연산
    - 삭제 연산의 수행 결과로 삭제된 원소를 Delete_q 연산자의 호출 프로그램에 반환한다.

>## <span style='color:#1E90FF'>원형 큐</span>
- 돌아가면서 비는 곳을 계속 쓸 수 있다라는 개념에서 나왔다.
- 배열로 구현한 큐의 경우 큐 원소의 개수가 n - 1이 아니더라도 큐가 full이 될 수 있다.
    - 배열로 구현한 큐의 문제점을 해결하기 위해 원형 큐가 제안됨
- 원형 큐는 파이프의 입구와 출구 부분을 연결시킨 형태
- 연결된 부분의 데이터 공간을 연속적으로 사용하기 위해 나머지 연산자를 활용함
- 큐의 양 끝을 연결시켜서 원으로 만든 형태의 큐
