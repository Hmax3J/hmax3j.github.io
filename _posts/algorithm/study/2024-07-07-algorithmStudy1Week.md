---
title: "[코딩테스트 합격자 되기 스터디] 1주차 - 시간 복잡도 (7.5 ~ 7.13)"
date: 2024-07-07 09:35:00 AM +09:00
categories: [Algorithm, Study]
tags: [java, algorithm, study]
---
***

>## <span style='color:#1E90FF'>코딩테스트 합격자 되기 스터디 1주차 시작</span>
코딩테스트 합격자 되기 스터디에 참여하게 되었다. 내가 하고 싶어 신청한 만큼 초심을 잃지말자. <br>
스터디가 끝났을 때는 더 성장한 나를 볼 수 있길... <br>
스터디 방법은 강의 보기 -> 해당되는 부분 책 다시 읽기 -> 블로그 정리 <br>
강의는 C++로 되어 있지만 개념적인 내용이라 언어 상관 없이 보고 코드는 각 언어에 맞게 바꾸면 된다. <br>

>## <span style='color:#1E90FF'>참고 강의 및 책</span>
인프런 : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 인프런 강의 링크</a> <br>
Youtube : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 Youtube 링크</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000210881884' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213087020' target='_blank' style='color:red'>코딩테스트 합격자 되기 C++ 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213641007' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바스크립트 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000212576322' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바 편</a> <br>

>## <span style='color:#1E90FF'>알고리즘이란?</span>
- 입력 값을 통해 출력 값을 얻기 위한 과정 <br>
- 어떠한 문제를 해결하기 위한 동작들의 모임 <br>
- 문제를 해결하기 위한 단계적인 방법 <br>

>## <span style='color:#1E90FF'>알고리즘의 조건</span>
- 각 단계가 명확해야 한다. <br>
- 구현할 수 있고, 실용적이어야 한다. <br>
- 입력 값, 출력 값이 있어야 한다. <br>
- 무한 루프가 되지 않고 종료가 되어야 한다. <br>
- 특정한 경우에만 적용되지 않고 모든 경우에 사용할 수 있어야 한다. <br>

>## <span style='color:#1E90FF'>알고리즘 성능</span>
- 절대시간 측정
    - 입력 값부터 출력 값 까지 시간을 측정한다.
    - PC에 따라 성능이 바뀔 수 있다.
- 연산횟수 측정
    - 객관적인 지표로 사용 가능하다.
    - 최악의 기준으로 연산횟수를 측정한다.
- 코딩테스트에서 알고리즘의 성능은 연산횟수로 측정한다. <br>
- 입력 값에 따라 연산횟수가 다르면, 가장 최악의 경우를 기준으로 연산횟수를 측정한다. <br>
- 입력 값에 따른 연산횟수를 측정해 알고리즘 성능을 지표로 나타내는 것을 시간 복잡도라고 한다. <br>

>## <span style='color:#1E90FF'>점근적 표기법</span>
- 내가 작성한 코드의 성능이 어느 정도 복잡한지 대략적으로 알면 충분하다. <br>
- N^2 + 3N + 5을 기준으로 N이 무한이라면 N^2에 비해 나머지들이 무시할 정도로 적은 값이 된다. <br>
- 정확한 연산횟수가 아닌, 연산횟수의 추이를 활용해 시간 복잡도를 표기하는 방법이다. <br>
- 최악의 경우를 고려해서 점근적 표기법으로 나타내는 것을 Big-O 표기라고 한다.
    - O(n^2) ...
- 다항식에서 가장 많이 영향을 미치는 항을 남기고 제거
    - N^2 + 3N + 5 에서 N^2 빼고 나머지는 제거
- 마지막 남은 항의 계수를 제거
    - N^2이 만약 3N^2 이라면 3은 제거하고 N^2만 남긴다.
- 최고차항 구하고 빅오 표기법으로 표기하기
    - ![algorithm-study](/assets/img/postImg/algorithm/study/1Week/Priority.JPG)
- 위 우선 순위에 따라 최고 차항을 제거한다. <br>
- 우선 순위가 낮을 수록 즉 1에 가까울 수록 복잡한 함수다. <br>
- ![algorithm-study](/assets/img/postImg/algorithm/study/1Week/AsymptoticNotation.JPG) <br>
- x가 충분히 큰 상태에서 비교한다. 그래서 팩토리얼이 지수 함수보다 값이 커질 수 밖에 없다. <br>

>## <span style='color:#1E90FF'>자주 보이는 복잡도</span>
- 1차원 배열 탐색 O(N) <br>
- 2차원 배열 탐색 O(N*M) <br>
- 이진탐색트리에서 원소 탐색 O(log N)
    - 매번 탐색 대상이 절반씩 줄어드는 경우 O(log N)이 된다.
- 동전 N개를 던졌을 때 경우의 수 O(2^N)
    - 2개를 던졌을 때 앞앞, 앞뒤, 뒤앞, 뒤뒤 총 4개의 경우의 수 O(2^N)

>## <span style='color:#1E90FF'>점근적 표기법 활용</span>
- 입력 값의 크기를 통해 어느정도 시간 복잡도 까지 허용되는지 추측 가능하다.
    - 구현시 알고리즘, 자료구조 선택을 명확히 할 수 있다.
    - 내가 구현하는 코드가 시간 초과 발생할 것인지 미리 파악이 가능하다.
    - 입력 값이 100만이 들어올 경우 O(NlogN), O(N), O(logN) 알고리즘을 사용할 수 있다.
- ![algorithm-study](/assets/img/postImg/algorithm/study/1Week/TimeComplexity.JPG) <br>

>## <span style='color:#1E90FF'>마치며</span>
시간 복잡도에 대해서는 문제에서 입력 값이 클 경우에는 <br>
O(N^2)을 쓰면 안된다 정도의 내용만 알고 있었는데 이번에 공부를 하며 어느 정도 감을 잡게 되었다. <br>
