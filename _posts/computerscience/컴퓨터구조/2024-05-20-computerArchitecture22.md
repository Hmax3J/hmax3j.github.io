---
title: "CPU, 스택과 함수 호출, 시스템 호출, 스레드 전환, 인터럽트 처리"
date: 2024-05-20 11:30:00 PM +09:00
categories: [ComputerScience, 컴퓨터구조]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>컴퓨터 시스템</span>
- 컴퓨터 시스템에는 함수 호출, 시스템 호출, 프로세스 전환, 스레드 전환, 인터럽트 처리 등 프로그래머에게 익숙하면서도 신비로운 구조들이 있다. <br>
- 함수 호출로 코드 재사용성 개선, 시스템 호출로 운영 체제에 요청, 프로세스와 스레드 전환으로 다중 작업이 가능할 뿐만 아니라 인터럽트 처리로 운영 체제가 외부 장치를 관리하게 할 수 있다. <br>

>## <span style='color:#1E90FF'>레지스터</span>
- 속도 때문에 필요하다. <br>
- 레지스터와 메모리는 본질적으로 차이가 없다. 둘 다 정보를 저장하는데 사용한다. <br>

>## <span style='color:#1E90FF'>스택 포인터</span>
- 실행되는 모든 함수는 스택 프레임을 갖는다. <br>
- 스택의 가장 중요한 정보는 스택 상단, 스택 상단 정보는 스택 하단을 가리키는 스택 포인터에 저장 <br>
- 함수가 실행될 때 함수에 정의된 로컬 변수와 전달된 매개변수 등을 저장하는 독립적인 메모리 공간을 스택프레임이라고 한다. <br>
- 함수 호출 단계가 깊어질수록 스택 프레임 수 증가, 호출이 완료되면 스택 프레임 수 감소 <br>
- 지금 어떤 명령어를 실행하고 있는지에 대한 정보가 매우 중요하다. 이 정보는 명령어 주소 레지스터가 가지고 있다. <br>

>## <span style='color:#1E90FF'>명령어 주소 레지스터</span>
- 명령어 주소 레지스터는 이름이 여러 개다. <br>
- 대다수 프로그래머는 프로그램 카운터, 줄여서 PC라고 부른다. <br>
- x86에서는 명령어 포인터, 줄여서 IP라고 부른다. <br>
- 프로그램이 실행되면 첫 번째로 실행할 기계 명령어의 주소가 PC 레지스터에 저장된다. <br>
- CPU는 이 PC 레지스터에 저장되어 있는 주소에 따라 메모리에서 명령어를 가져와 실행한다. <br>
- 일반적으로 명령어는 순차적으로 실행된다. PC 레지스터 값은 순차적으로 증가한다. <br>
- 제어 이전과 관련된 일부 기계 명령어는 새로운 명령어 주소를 PC 레지스터에 저장한다.
    - 분기 점프, 함수 호출과 반환 등이 이에 해당한다. <br>
- CPU의 PC 레지스터를 제어하는 것은 CPU의 실행 흐름을 장악하는 것이며, 기계 명령어가 직접 실행 상태에 따라 CPU가 다음에 어떤 명령어를 실행해야 하는지 결정할 수 있게 된다. <br>

>## <span style='color:#1E90FF'>상태 레지스터</span>
- 수행 중에 자리 올림수가 발생하거나 넘침이 발생할 수 있는데 이런 정보가 상태 레지스터에 저장된다. <br>
- CPU는 기계 명령어를 실행할 때 커널 상태와 사용자 상태 두 가지 상태를 가진다. <br>
- 자신이 작성한 응용 프로그램은 모두 사용자 상태에서 실행된다. <br>
- 사용자 상태에서는 제약이 있지만, 커널 상태에서 CPU는 어떤 명령어도 실행할 수 있다. <br>
- CPU가 현재 어떤 상태에서 동작 중인지 표시하는 특정한 비트가 있다. <br>
- 상태 레지스터 값을 바꾸어 CPU 동작 상태를 변경할 수 있다. CPU가 사용자 상태와 커널 상태 사이를 전환한다. <br>

>## <span style='color:#1E90FF'>상황정보</span>
- 레지스터를 통해 프로그램이 실행된 직후부터 현시점까지 세세한 단면을 알 수 있으며, 현시점에 레지스터에 저장된 모든 정보를 일반적으로 상황 정보라고 한다. <br>
- 프로그램의 실행 시 상황 정보를 가져오고 저장할 수 있다면 언제든지 프로그램의 실행을 일시 중지할 수 있으며, 언제든지 프로그램의 실행을 재개할 수 있다. <br>
- 상황 정보를 저장하고 복원해야 하는 이유는 무엇인가
    - 근본적인 원인은 CPU가 엄격한 오름차순으로 기계 명령어를 실행하지 않기 때문이다.
    - CPU는 함수 A에서 함수 B로 점프할 수 있다.
    - CPU는 커널 코드를 실행하기 위해 사용자 상태에서 커널 상태로 전환할 수 있다.
    - CPU는 프로그램 A의 기계 명령어 실행 상태에서 프로그램 B의 기계 명령어 실행 상태로 전환할 수 있다.
    - CPU는 인터럽트를 처리하기 위해 실행하던 프로그램을 중지시킬 수 있다. <br>
- 이 상황 중 어느 것도 CPU에 의한 기계 명령어의 순차적 실행을 방해할 수 없으며, 이때 CPU는 이후 복구를 대비해서 중단되기 전 상태를 저장해야 한다. <br>
- 네 가지 상황은 함수 호출, 시스템 호출, 스레드 전환, 인터럽트 처리이며 프로그램 실행의 기반이다. <br>

>## <span style='color:#1E90FF'>중첩과 스택</span>
- A는 B에 의존하고, B는 C에 의존한다. 이 때문에 C의 처리가 완료되어야 B로 돌아올 수 있고, B의 처리가 완료되어야 A로 돌아올 수 있다. 가장 먼저 시작한 작업이 가장 마지막에 완료된다. <br>
- 스택은 이런 중첩 구조를 처리하기 위해 탄생했다. <br>

>## <span style='color:#1E90FF'>시스템 호출과 커널 상태 스택</span>
- 응용 프로그램은 시스템 호출을 통해 운영 체제에 서비스를 요청한다. <br>
- 운영 체제가 시스템 호출을 완료하는 데 필요한 실행 시간 스택은 커널 상태 스택에 있다. <br>
- 본래 모든 사용자 상태 스레드는 커널 상태에 대응하는 커널 상태 스택을 가지고 있다. <br>

>## <span style='color:#1E90FF'>인터럽트와 인터럽트 함수 스택</span>
- 현재 CPU 실행 흐름을 끊고 특정 인터럽트 처리 함수로 점프하며, 인터럽트 처리 함수의 실행이 완료되면 원래 위치로 다시 점프한다. <br>
- 시스템 호출은 사용자 상태 프로그램이 직접 실행하는데, 인터럽트 처리는 외부 장치로 실행된다는 차이점이 있다. <br>
- CPU가 사용자 상태에서 모든 기계 명령어를 실행할 때마다 인터럽트가 발생할 수 있다. <br>