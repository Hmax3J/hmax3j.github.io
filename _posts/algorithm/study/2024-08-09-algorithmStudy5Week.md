---
title: "[코딩테스트 합격자 되기 스터디] 5주차 - 집합 (8.4 ~ 8.10)"
date: 2024-08-09 01:00:00 AM +09:00
categories: [Algorithm, Study]
tags: [java, algorithm, study]
---
***

>## <span style='color:#1E90FF'>코딩테스트 합격자 되기 스터디 5주차</span>
강의 보기 -> 해당되는 부분 책 다시 읽기 -> 블로그 정리 <br>
강의는 C++로 되어 있지만 개념적인 내용이라 언어 상관 없이 보고 코드는 각 언어에 맞게 바꾸면 된다. <br>

>## <span style='color:#1E90FF'>참고 강의 및 책</span>
인프런 : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 인프런 강의 링크</a> <br>
Youtube : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 Youtube 링크</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000210881884' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213087020' target='_blank' style='color:red'>코딩테스트 합격자 되기 C++ 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213641007' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바스크립트 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000212576322' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바 편</a> <br>

>## <span style='color:#1E90FF'>상호배타적 집합</span>
- 교집합이 없는 집합관계
    - 2개가 아니라 N개일 수 있다.
- 집합 A의 원소는 {1, 2, 3}, 집합 B의 원소는 {4, 5, 6}, 집합 C의 원소는 {7, 8, 9}
    - A, B, C의 교집합이 없기 때문에 상호배타적 집합이다.
- 집합 A의 원소는 {1, 2, 3}, 집합 B의 원소는 {2, 4, 6}
    - A의 {2}, B의 {2}가 있기 때문에 상호배타적 집합이 아니다.

>## <span style='color:#1E90FF'>집합 표현하기</span>
- 특정 집합 원소들이 하나의 집합의 원소라는 것을 알 수 있어야 함
    - 집합 A = {1, 2, 3} 일 때 각 원소가 집합 A에 속한다는 걸 알아야 함
    - ```java
        public static void main(String[] args) {
            int[] A = {1, 2, 3};
            System.out.println(isElementInArray(A, 1)); // true
            System.out.println(isElementInArray(A, 2)); // true
            System.out.println(isElementInArray(A, 3)); // true
            System.out.println(isElementInArray(A, 4)); // false
        }
        public static boolean isElementInArray(int[] array, int value) {
            for (int element : array) {
                if (element == value) {
                    return true; // 값이 발견되면 true 반환
                }
            }
            return false; // 값이 발견되지 않으면 false 반환
        }
    ```
- 각 집합간 다른 집합이라는 것을 알 수 있어야 함
    - 서로 다른 집합이란 두 집합이 완전히 같은 원소를 갖지 않을 때를 의미
    - 집합 A = {1, 2, 3}, B = {4, 5, 6} 일 때 두 집합이 다른 집합이란걸 알아야 함
    - 두 집합간의 교집합이 있어도 교집합을 제외한 원소들이 다르면 서로 다른 집합
- 특정 원소가 어느 집합에 속하는지 알 수 있어야 함
    - 집합 A = {1, 2, 3}, B = {4, 5, 6} 일 때 원소 5가 집합 B에 속한다는 걸 알아야 함
    - ```java
        public static void main(String[] args) {
            int[] B = {4, 5, 6};
            boolean isGood = false;
            int target = 5;
            for (int i = 0; i < B.length; i++) {
                if (target == B[i]) {
                    isGood = true;
                    break;
                }
            }
            if (!isGood) {
                System.out.println("5는 B에 속하지 않는다.");
            } else {
                System.out.println("5는 B에 속한다.");
            }
        }
    ```
- 두 개의 집합을 하나로 합칠 수 있어야 함
    - 집합 A = {1, 2, 3}, B = {4, 5, 6} 일 때 {1, 2, 3, 4, 5, 6}으로 만들 수 있어야 함
    - 두 개의 집합의 원소들을 모두 포함하는 새로운 집합을 만들 수 있어야 한다는 의미
    - 새로운 집합에는 원래 집합들의 모든 원소가 포함되며, 중복된 원소는 제거되고 이를 합집합이라 함
- 집합을 구현할 때 이 정도는 고려하고 구현을 해야한다. <br>

>## <span style='color:#1E90FF'>집합 표현하기 - 대표 원소</span>
- 각 집합에서 가장 작은 원소를 대표 원소(루트 노드)로 한다.
    - 대표 원소는 현재 노드와 부모 노드가 같다.
    - 배열을 활용해서 나타낼 수 있다. (현재 노드는 인덱스, 부모 노드는 값)
    - 부모 노드가 없다면 자기 자신을 기록한다.
    - 집합에 없는 노드는 배열의 해당하는 인덱스를 -1로 기록한다.

>## <span style='color:#1E90FF'>집합의 연산 - find</span>
- 특정 노드의 루트 노드를 확인하는 연산
    - 특정 노드로부터 루트 노드가 나올 때 까지 거슬러 올라간다.
    - union 연산에서도 활용된다.
- 집합 A = {1, 2, 3, 4, 5, 6, 7}
    - 부모1 - 자식2,3,5 | 부모2 - 자식4,6 | 부모6 - 자식7
    - 배열로 나타내면 1, 1, 1, 2, 1, 2, 6 이다.
    - 1번 노드 ~ 7번 노드까지 이다.
- find(7)을 하면 노드 7의 값(부모 노드)를 확인한다.
    - 노드7과 값인 6은 다르다. 노드와 값이 같을 때 까지 반복한다.
    - 노드와 값이 같아야 루트 노드다.
    - 7의 부모 노드는 6이다. find(6)을 한다.
    - 6의 부모 노드는 2다. find(2)를 한다.
    - 2의 부모 노드는 1이다. find(1)을 한다.
    - 1의 부모 노드는 없으니 자기 자신인 1이다.
    - 노드7의 루트 노드는 1이다.
- 거쳐간 부모 노드의 값을 바꾸는 방법과 루트 노드를 찾을 경우 바로 리턴하는 방법 2가지가 있다. <br>
- 루트 노드를 찾는데 필요한 경로가 깊어질 경우 연산 횟수가 증가한다. O(N) <br>
- 경로의 깊이를 줄이는 방법이 거쳐간 부모 노드의 값을 바꾸는 방법이다.
    - 이 방법을 경로 압축 알고리즘이라고 한다.
    - 1 -> 2-> 3-> 4-> 5 이렇게 되면 깊이가 4다. 이것을 경로 압축 알고리즘으로 바꾸어보자.
    - 1 - 2, 1 - 3, 1 - 4, 1 - 5 경로 압축 알고리즘으로 바꾸었을 때 상황이다.
    - 이렇게 되면 깊이가 1이다. 전부 한 번에 찾을 수 있다.
    - 이런 이유 때문에 경로 압축 알고리즘을 사용한다.
- 경로 압축 호출 과정
    - find(5), disjoint[5] = disjoint[4] 이후, disjoint[5] 반환
    - find(4), disjoint[4] = disjoint[3] 이후, disjoint[4] 반환
    - find(3), disjoint[3] = disjoint[2] 이후, disjoint[3] 반환
    - find(2), disjoint[2] = disjoint[1] 이후, disjoint[2] 반환
    - find(1), 루트 노드이므로 disjoint[1] 반환
- 경로 압축을 하더라도 모두 깊이를 1로 만들어 주지 않는다. 거쳐간 경로만 깊이를 1로 만든다. <br>

>## <span style='color:#1E90FF'>집합의 연산 - union</span>
- 두 개의 집합을 하나의 집합으로 합치는 연산
    - 상호배타적 집합을 합친다.
- find 연산을 통해 각 집합의 대표 원소(루트 노드)를 구하고, 루트노드를 하나로 통일한다.
    - 여러가지 방법이 있지만 가장 간단한 방법은 작은 루트 노드 쪽으로 합친다.
- 집합 A = {1, 2, 3, 8}, B = {4, 5, 6}
    - union(6, 8) 수행
    - find(6), find(8)을 통해 루트 노드를 확인한다.
    - find(8) = 1, find(6) = 4, find(8) < find(6)
    - 두 집합의 대표 원소를 find(8)인 1로 통일한다.

>## <span style='color:#1E90FF'>집합의 연산 - 효율성에 대한 고민</span>
- union 연산 이후 깊이를 최소화 할 수 있을까?
    - 집합에 랭크를 도입한다. (특정 노드 기준 최대 깊이)
    - 랭크가 더 큰 쪽으로 합쳐, 랭크의 증가를 최소화한다. (랭크 기반 알고리즘)
- 랭크 개념
    - 현재 노드 기준 트리 최대 깊이
    - 부모1 - 자식2,3,5 | 부모2 - 자식4,6 | 부모6 - 자식7
    - 노드1의 경우 1 -> 2 -> 6 -> 7이 최대 깊이 이므로 랭크는 3
    - 노드3, 4, 5, 7은 자신을 제외하고 더 이상 내려갈 곳이 없으므로 랭크 0
    - 노드 2의 경우 2 -> 6 -> 7이 최대 깊이 이므로 랭크는 2
    - 루트 노드의 랭크가 가장 높다. 랭크 기반 알고리즘은 루트 노드의 랭크 기준
    - 루트 노드의 랭크를 낮게 유지하는 방향으로 합치는 것이 전략
- 집합 A = 부모1 - 자식2,3 | 부모2 - 자식4
    - 1 -> 2 -> 4로 랭크가 2
- 집합 B = 부모5 - 자식6,7
    - 5 -> 6, 5 -> 7로 랭크가 1
- 랭크가 더 높은 쪽으로 합친 경우
    - 부모1 - 자식2,3 | 부모2 - 자식4 | 부모5 - 자식6,7
    - 1 -> 2 -> 4, 1 -> 5 -> 6, 1 -> 5 -> 7로 랭크가 2
- 랭크가 더 낮은 쪽으로 합친 경우
    - 부모5 - 자식1,6,7 | 부모1 - 자식2,3 | 부모2 - 자식4
    - 5 -> 1 -> 2 -> 4 로 랭크가 3
- 랭크가 더 높은 쪽으로 합친 경우가 깊이가 더 얕다.
    - 랭크가 더 높은 쪽의 깊이가 이미 깊기 때문에 합칠 때 더 깊어지지 않는다.
    - 그래서 랭크가 더 높은 쪽으로 합쳐야 한다.

>## <span style='color:#1E90FF'>집합의 구현</span>
- 노드의 최대 값이 크지 않은 경우
    - 배열로 구현
- 노드의 최대 값이 큰 경우
    - unordered_map으로 구현 (C++)
    - 자바는 HashMap으로 구현

>## <span style='color:#1E90FF'>집합 알고리즘의 사용</span>
- 네트워크 연결성 확인에서 사용한다.
    - 대규모 네트워크에서 두 컴퓨터가 서로 연결되어 있는지 확인
- 주어진 노드와 연결된 간선으로 이루어진 네트워크에서 두 노드가 서로 연결되어 있는지 확인하는 문제
    - 입력값 : 5(노드의 최대값), 3(간선의 개수), 0 1, 1 2, 3 4 (간선), 2(쿼리의 개수), 0 2, 0 3 (쿼리)
    - 출력값 : 1 <- 연결됨(0, 2), 0 <- 연결되지 않음(0, 3)

>## <span style='color:#1E90FF'>섬 연결하기 문제 풀이</span>
- <a href='https://school.programmers.co.kr/learn/courses/30/lessons/42861' target='_blank' style='color:red'>섬 연결하기</a> <br>
- ```java
```