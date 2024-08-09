---
title: "메모리 읽기와 쓰기 방식으로 파일 처리"
date: 2024-05-27 09:30:00 PM +09:00
categories: [ComputerScience, 컴퓨터구조]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>파일과 가상 메모리</span>
- 가상 메모리의 목적은 모든 프로세스가 각자 독점적으로 메모리를 소유하고 있다고 생각하게 하는 것이다. <br>
- 프로세스가 만나는 주소 공간은 가상이기 때문에 모든 것을 다루기 편하다. <br>
- 파일은 개념적으로 연속된 디스크 공간에 저장되어 있다고 생각할 수 있다. <br>

>## <span style='color:#1E90FF'>큰 파일 처리</span>
- mmap는 메모리를 직접 읽고 쓰는 것처럼 디스크의 파일을 사용할 수 있어 편리하다. <br>
- mmap를 사용하여 제한된 물리 메모리임에도 매우 큰 파일을 처리할 수 있다. <br>