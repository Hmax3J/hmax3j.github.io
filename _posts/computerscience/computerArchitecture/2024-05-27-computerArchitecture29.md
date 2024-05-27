---
title: "파일을 읽을 때 프로그램에 생기는 일"
date: 2024-05-27 07:30:00 PM +09:00
categories: [ComputerScience, ComputerArchitecture]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>메모리 관점에서 입출력</span>
- 메모리 관점에서 입출력은 단순한 메모리의 복사다. <br>
- 데이터가 외부 장치에서 메모리로 복사되면 입력(input), 메모리에서 외부 장치로 복사되면 출력(output) <br>
- 메모리와 외부 장치 사이에 복사 데이터를 주고 받는 것을 입출력이라 하고 약어로 I/O라고 한다. <br>

>## <span style='color:#1E90FF'>프로그램이 파일을 읽는 과정</span>
- 일반적으로 입출력 데이터는 운영 체제 내부로 먼저 복사되며 이후 운영 체제가 프로세스의 주소공간으로 복사한다. <br>
- 운영 체제를 우회하여 직접 데이터를 프로세스 주소 공간에 복사할 수 도 있는데, 이를 무복사 기법이라고 한다. <br>