---
title: "복잡 명령어 집합의 반격"
date: 2024-05-20 11:00:00 PM +09:00
categories: [ComputerScience, 컴퓨터구조]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>RISC와 동일한 CISC</span>
- RISC(Reduced Instruction Set Computer) 축소 명령어 집합 컴퓨터 <br>
- CISC(Complex Instruction Set Computer) 복잡 명령어 집합 컴퓨터 <br>
- 복잡 명령어 집합은 명령어 실행 시간이 고르지 않아 파이프라인을 활용할 수 없었다. <br>
- 복잡 명령어 집합의 명령어를 CPU 내부에서 축소 명령어 집합의 간단한 명령어로 변환했다. <br>
- 이 축소 명령어 집합의 간단한 명령어와 유사한 명령어들을 마이크로 명령어라고 한다. <br>
- 이 방식은 복잡 명령어 집합의 호환성을 유지하면서 동시에 축소 명령어 집합의 장점을 얻을 수 있다. <br>

>## <span style='color:#1E90FF'>하이퍼 스레딩</span>
- 하이퍼 스레딩은 하드웨어 스레드라고도 한다. <br>
- 물리적으로 CPU 코어가 하나지만 논리적으로 CPU 코어가 여러 개로 인식하는 것을 하이퍼 스레딩이라 한다. <br>