---
title: "메모리 장벽"
date: 2024-05-25 11:30:00 PM +09:00
categories: [ComputerScience, 컴퓨터구조]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>들어가기 전 퀴즈</span>
```
thread1    thread2
X = 1;      Y = 1;
a = y;      b = X;
```
- 두 전역 변수 X, Y가 0으로 초기화 되어 있고 스레드 두 개가 있을 때 위 코드를 실행 했을 때 결과는? <br>
    - 스레드 1이 먼저 실행되며, 이때 a = 0, b = 1
    - 스레드 2가 먼저 실행되며, 이때 a = 1, b = 0
    - 스레드 1과 스레드 2가 동시에 코드의 첫 줄을 실행하며, 이때 a = 1, b = 1 <br>
- x86 플랫폼에서는 네 번째 상황이 있을 수 있다. a와 b가 모두 0일 수도 있다. <br>
- 코드가 비순차적으로 실행되는 것처럼 보이는 이유는 뒤에서 알아보도록 한다. <br>

>## <span style='color:#1E90FF'>컴파일러와 OoOE</span>
- 멍령어의 비순차적 실행의 단계
    - 기계 명령어를 생성하는 단계: 컴파일 중에 명령어를 재정렬한다.
    - CPU가 명령어를 실행하는 단계: 실행 중에 명령어가 비순차적으로 실행된다. <br>
- 지금까지 CPU의 작업 과정
    - 기계 명령어를 가져온다.
    - 명령어의 피연산자가 레지스터에 저장되는 등 이미 준비 완료 상태라면 명령어는 실행단계에 들어간다.
    - 명령어의 피연산자가 아직 메모리에서 레지스터로 저장되지 않아 준비가 완료되지 않았다면, CPU는 피연산자가 메모리에서 레지스터로 저장될 때까지 기다려야 한다. CPU 속도에 비해 메모리의 접근 속도가 매우 느리기 때문이다.
    - 데이터가 이미 준비되었다면 명령어가 실행되기 시작한다.
    - 실행 결과를 다시 기록한다. <br>
- 개선된 CPU의 작업 과정
    - 기계 명령어를 가져온다.
    - 명령어를 대기열에 넣고 명령어에 필요한 피연산자를 읽는다.
    - 명령어는 대기열에서 피연산자의 준비가 완료될 때까지 대기한다. 이때 준비가 완료된 명령어가 먼저 실행 단계에 들어갈 수 있다.
    - 기계 명령어를 실행하면 실행 결과를 대기열에 넣는다.
    - 이전 명령어의 실행 결과가 기록될 때까지 기다렸다가 현재 명령어의 실행 결과를 기록한다. 이유는 명령어의 원래 실행 순서에 따라 유효한 결과를 얻기 위한 것이다. <br>
- 이 과정에서 명령어 실행은 엄격한 순서대로 진행되지 않으며 이것이 비순차적 명령어 처리(OoOE)다. <br>
- CPU와 메모리 사이의 속도 차이가 크기 때문에 엄격한 순서대로 실행하면 명령어가 의존하는 피연산자를 기다리는 동안 파이프라인 내부에 빈 공간인 슬롯이 생긴다. <br>
- 비순차적 명령어 실행 기능이 있는 CPU에서는 명령어가 비순차적으로 실행될 수 있지만, 모든 CPU가 이 기능을 가지고 있지는 않다. <br>

>## <span style='color:#1E90FF'>캐시 고려</span>
- L1, L2 캐시는 각각의 CPU 코어마다 별도로 존재하며, L3 캐시와 메모리는 모든 코어가 공유한다. <br>
- 캐시가 있는 모든 시스템은 반드시 캐시 갱신과 캐시 일관성을 유지시키느냐에 대한 문제를 겪는다. <br>
- 이 과정은 비교적 시간을 많이 소모하고, 이 작업 전에 CPU는 반드시 대기 상태를 중지해야 한다. <br>
- 이 과정을 최적화하기 위해 일부 시스템은 저장 버퍼 등 대기열을 추가한다. <br>
- 기록 작업이 있을 때 대기열에 직접 기록하기 때문에 캐시는 즉시 갱신되지 않는다. <br>
- CPU는 캐시가 갱신되기를 기다리지 않고 다음 명령어를 계속 실행할 수 있다. <br>
- 비순차적 실행은 자기 자신 이외의 또 다른 코어가 해당 코어를 바라볼 때만 나타나는 현상이다. <br>
- 단일 스레드 환경에서 프로그래밍할 경우, 근본적으로 이 문제를 신경 쓸 필요가 없다. <br>

>## <span style='color:#1E90FF'>네 가지 메모리 장벽 유형</span>
- LoadLoad <br>
- StoreStore <br>
- LoadStore <br>
- StoreLoad <br>

>## <span style='color:#1E90FF'>획득-해제 의미론</span>
- 다중 스레드 프로그래밍을 사용할 때 프로그래머는 두 가지 문제를 겪는다.
    - 공유 데이터에 대한 상호 배타적인 접근
    - 스레드 간 동기화 문제 <br>
- 획득-해제 의미론은 두 번째 문제를 해결하는데 사용되지만, 공식적인 획득-해제 의미론 정의는 존재하지 않는다. <br>
- 획득 의미론
    - 메모리 읽기 작업에 대한 것
    - LoadLoad, LoadStore <br>
- 해제 의미론
    - 메모리 쓰기 작업에 대한 것
    - StoreStore, LoadStore <br>

>## <span style='color:#1E90FF'>다른 CPU, 다른 천성</span>
- 모든 유형의 CPU에 이런 명령어 재정렬이 있는 것은 아니다. <br>

>## <span style='color:#1E90FF'>잠금 없는 프로그래밍</span>
- 잠금 없는 프로그래밍을 해야 할 때만 명령어 재정렬에 신경 쓰면 된다. <br>
- 공유 변수가 잠금 보호 없이 여러 스레드에서 사용될 때 발생한다. <br>