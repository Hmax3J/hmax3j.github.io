---
title: "콜백 함수, 클로저, 컨테이너, 가상 머신 기술"
date: 2024-05-14 00:00:00 AM +09:00
categories: [ComputerScience, ComputerArchitecture]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>함수</span>
- 특정 언어에서 코드를 할당, 사용, 매개변수로 전달, 반환값으로 사용 등 일반 변수를 다루듯이 처리할 수 있을 때 일급 객체 함수라고 한다. <br>
- 함수가 다른 함수에 매개변수로 전달될 때 해당 함수를 콜백 함수라고 한다. <br>

>## <span style='color:#1E90FF'>클로저</span>
- 콜백 함수는 코드 정의는 A에서 하지만 호출은 B에서 하는 것처럼 정의와 호출을 서로 다른 곳에서 한다. <br>
```python
def add():
    b = 10
    def add_inner(x):
        return b + x
    return add_inner
f = add()
print(f(2))
```
- 위 코드에서 add 함수와 add_inner 함수를 정의한다. <br>
- 이 함수는 두 가지 데이터를 사용한다. add 함수 내에 정의된 b와 사용자가 전달하는 매개변수로 2가 그 값에 해당된다. print 함수로 f 함수가 호출되어야 add_inner 함수에 필요한 모든 데이터를 얻을 수 있다. <br>
- 여기서 add_inner 함수는 단순한 코드일 뿐만 아니라 실행 시간 환경인 b 변수를 묶어서 전달하는 클로저이다. <br>
- 콜백 함수를 일부 데이터와 한데 묶어 변수로 취급할 때 클로저가 탄생한다. <br>

>## <span style='color:#1E90FF'>컨테이너</span>
- 어떤 함수가 CPU를 능동적으로 일시 중지하고 다음에 함수가 다시 호출될 때 앞에서 중단된 지점에서 계속 실행하는 것이 가능할 때, 이 함수가 코루틴에 해당된다. <br>
- 함수의 일시 중지와 재개가 커널 상태에서 구현되는 경우에는 이를 스레드라고 한다. <br>
- 스레드에 주소 공간처럼 종속된 실행 시 리소스를 결합한 것이 프로세스다. <br>
- 프로그램이 구성, 라이브러리처럼 프로그램이 의존하는 실행 환경과 함께 묶인 것을 컨테이너라고 한다. <br>
- 컨테이너라는 단어를 사용할 때는 선박 배송 등에서 쓰는 수송 용기를 지칭한다. 이 선적 컨테이너가 주는 이점을 살펴보자.
    - 컨테이너는 서로 격리되어 있다.
    - 장시간 반복 사용이 가능하다.
    - 적재와 하역이 빠르다.
    - 항구와 선박에서 사용되는 표준 크기로 구성되어 있다.
- 컨테이너와 선적 컨테이너는 개념상 매우 유사하다. <br>
- 프로그램을 작성했을 때 프로그램을 실행하려면 서비스를 비롯한 몇 가지 시스템 라이브러리와 설정을 구성하는 파일이 필요하다. 이 프로그램을 다른 사람이 사용하려면 각자 자신의 환경에 서비스를 설치 및 구성하고 시스템 라이브러리를 적재한 후 설정을 구성하는 파일을 작성해야 한다. <br>
- 프로그램과 프로그램에 필요한 서비스, 라이브러리, 설정 구성 파일을 한데 묶어 다른 사람들이 환경을 따로 구성할 필요 없이 바로 사용할 수 있는 방법을 찾다가 컨테이너 기술이 탄생했다. <br>
- 컨테이너는 일종의 가상화 기술로서 운영 체제를 가상화 한다. <br>
- 컨테이너는 운영 체제에서 제공하는 기능을 이용하여 프로세스를 격리하고 CPU, 메모리, 디스크에 대한 접근을 제어하는 방식으로, 컨테이너에 포함된 프로세스가 전체 운영 체제 안에서 자기 자신의 프로세스만 존재하고 있다고 간주하게 한다. <br>
- 컨테이너는 운영 체제 계층 수준에서 소프트웨어 리소스를 가상화한다. <br>
- 가상화 기술은 소프트웨어를 이용하여 컴퓨터의 하드웨어를 추상화하고, 하드웨어 리소스를 가상 컴퓨터 여러 개로 나눈다. 그 위에서 운영 체제를 실행하면 이 운영 체제는 하드웨어의 리소스를 가져와 사용할 수 있게 된다. 가상 머신 감시자가 이런 작업을 하는 소프트웨어로, 흔히 이를 하이퍼바이저라고 한다. <br>

>## <span style='color:#1E90FF'>가상머신</span>
- 가상 머신 감시자에서 실행되는 운영 체제를 가상 머신이라고 한다. <br>
- 가상 머신 감시자에서 실행되는 운영 체제는 하드웨어 리소스를 독점한다고 간주한다. <br>
- CPU의 가상화는 생성되는 모든 프로세스가 자신이 CPU를 독점적으로 소유하고 있다고 생각한다. <br>
- 메모리 가상화는 가상 메모리 내 프로세스가 자신이 메모리를 독점적으로 소유하고 있다고 생각한다. <br>