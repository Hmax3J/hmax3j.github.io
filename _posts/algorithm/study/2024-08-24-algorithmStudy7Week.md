---
title: "[코딩테스트 합격자 되기 스터디] 7주차 - 백트래킹 (8.18 ~ 8.24)"
date: 2024-08-24 06:00:00 PM +09:00
categories: [Algorithm, Study]
tags: [java, algorithm, study]
---
***

>## <span style='color:#1E90FF'>코딩테스트 합격자 되기 스터디 7주차</span>
강의 보기 -> 해당되는 부분 책 다시 읽기 -> 블로그 정리 <br>
강의는 C++로 되어 있지만 개념적인 내용이라 언어 상관 없이 보고 코드는 각 언어에 맞게 바꾸면 된다. <br>
이번 주차가 일정의 마지막 주차인데 스터디 전체 참여율이 50%가 넘을 경우, <br>
다음 주차도 계속 진행한다고 한다! 다음 주차도 하면 좋겠다ㅎㅎ <br>

>## <span style='color:#1E90FF'>참고 강의 및 책</span>
인프런 : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 인프런 강의 링크</a> <br>
Youtube : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 Youtube 링크</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000210881884' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213087020' target='_blank' style='color:red'>코딩테스트 합격자 되기 C++ 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213641007' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바스크립트 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000212576322' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바 편</a> <br>

>## <span style='color:#1E90FF'>백트래킹</span>
- 가장 최근에 방문했던 노드로 다시 돌아간다. (예시 : DFS)
- 완전 탐색하지 말고, 내가 찾는 답일 가능성이 있는 경우에만 탐색한다.
    - 예를 들면, 노드의 값이 숫자의 합이고 찾는 숫자가 5일 경우
    - 탐색한 노드 값이 5를 초과했다면 다음 노드를 탐색해도 5를 초과한다.
    - 그래서 탐색을 진행해도 5를 찾을 수 없으므로 다시 돌아가 다른 곳을 탐색한다.
- 탐색을 진행할 때 유효한 판단을 하는 부분을 구현해야 한다.
    - 이를 유망함수를 구현한다고 한다.
    - 예를 들어, 외출할 때 집에 물건을 놓고 왔을 경우
    - 다른 집에는 내 물건이 있을 리가 없으니 이 부분을 제외한다.
    - 나의 집으로 돌아가 찾아야 한다.
    - 나의 집이 유망함수다.
- 백트래킹의 과정
    - 첫 번째, 상태 정의 : 문제의 각 단계에서 가능한 상태를 정의한다.
    - 두 번째, 유망 함수 : 현재 상태가 유망한 지 판단, 유망하지 않으면 탐색 정지
    - 세 번째, 해결책 확인 : 현재 상태가 문제의 해결책인지 판단한다.
    - 네 번째, 재귀 호출 : 유망한 상태로 이동하면서 문제를 해결한다.
- ```java
    // 유망성 판단 함수
    boolean isPromising(int level, State state) {
        // 현재 상태가 유망한지 판단하는 로직을 구현합니다.
        return true; // 예시로 true 반환, 실제로는 로직을 구현해야 합니다.
    }
                                                                        //
    // 해결책 확인 함수
    boolean isSolution(State state) {
        // 현재 상태가 문제의 해결책인지 판단하는 로직을 구현합니다.
        return true; // 예시로 true 반환, 실제로는 로직을 구현해야 합니다.
    }
                                                                        //
    // 해결책 처리 함수
    void processSolution(State state) {
        // 해결책을 처리하는 로직을 구현합니다.
    }
                                                                        //
    // 백트래킹 함수
    void backtrack(int level, State state) {
        // 현재 상태가 해결책이면 처리
        if (isSolution(state)) {
            processSolution(state);
            return;
        }
        // 다음 가능한 상태를 탐색
        for (State nextState : possibleStates(state)) {
            if (isPromising(level, nextState)) {
                backtrack(level + 1, nextState);
            }
        }
    }
```

>## <span style='color:#1E90FF'>백트래킹 예시 - 부분 합</span>
- {1, 2, 3, 4}로 이루어진 집합에서 숫자를 뽑아 합이 5인 조합 구하기
- 완전 탐색으로 풀 경우 O(2^N)를 가진다.
    - 2 * 2 * 2 * ... 2
- 백트래킹으로 접근하기
    - 상태 정의 : 현재까지 선택한 숫자들의 합
    - 유망 함수 : 현재 부분 합이 목표 값을 초과하면 유망하지 않다고 판단
    - 해결책 확인 : 현재 부분 합이 목표 값과 일치하는지 확인
    - 재귀 호출 : 다음 숫자를 선택하여 부분합 갱신
- ```java
    impor java.util.*;
                                                                        //
    public class CombinationFinder {
        // 사용할 숫자들
        private static List<Integer> nums = List.of(1, 2, 3, 4);
        // 목표 합
        private static int target = 5;
        // 현재 조합
        private static List<Integer> current = new ArrayList<>();
                                                                        //
        public static void main(String[] args) {
            findCombinations(0);
        }
                                                                        //
        private static void findCombinations(int index) {
            int sum = 0;
            for (int num : current) {
                sum += num;
            }
                                                                                        //
            // 조건 1: 현재 조합으로 합이 target이 되면 결과를 출력하고 더 탐색하지 않음
            if (sum == target) {
                for (int num : current) {
                    System.out.print(num + " ");
                }
                System.out.println();
                return;
            }
                                                                                        //
            // 조건 2: 합이 target을 초과하면 더 탐색하지 않음
            if (sum > target) {
                return;
            }
                                                                                        //
            // 유망한 경우에만 다음 숫자를 추가하여 탐색을 계속함
            for (int i = index; i < nums.size(); i++) {
                current.add(nums.get(i));
                findCombinations(i + 1);
                current.remove(current.size() - 1); // 현재 숫자를 조합에서 제외하여 다음 경우를 탐색
            }
        }
    }
```

>## <span style='color:#1E90FF'>백트래킹 예시 - N 퀸</span>
- 체스의 퀸을 N * N 체스판에 N개 배치했을 때 서로 공격할 수 없는 위치에 놓을 수 있는 방법의 경우의 수 확인
    - 퀸은 현재 자신 위치 기준 8방 직선방향으로 공격 가능
- 완전탐색으로 풀 경우 O(N^N)를 가진다.
- 백트래킹으로 접근하기
    - 상태 정의 : 각 행에 하나의 퀸이 위치하도록 한다.
    - 유망 함수 : 현재 행에 퀸을 놓았을 때, 다른 퀸과 충돌하는지 확인한다.
    - 해결책 확인 : 모든 퀸이 배치되었는지 확인
    - 재귀 호출 : 다음 행에 퀸을 배치
- ```java
    public class NQueens {
        // N Queen 문제: n x n 체스판에 n개의 퀸을 서로 공격하지 못하게 배치하는 문제
        private static final int N = 4; // 퀸의 개수
        private static int[] board = new int[N]; // 보드 배열, 인덱스는 행을, 값은 열을 나타냄
                                                                                            //
        // 보드의 현재 상태를 출력하는 함수
        private static void printBoard() {
            // 각 행을 반복
            for (int i = 0; i < N; ++i) {
                // 각 열을 반복
                for (int j = 0; j < N; ++j) {
                    // 현재 위치에 퀸이 있는지 확인
                    if (board[i] == j) {
                        System.out.print("Q "); // 퀸이 있으면 "Q" 출력
                    } else {
                        System.out.print(". "); // 퀸이 없으면 "." 출력
                    }
                }
                System.out.println(); // 한 행이 끝나면 줄바꿈
            }
            System.out.println(); // 보드 전체 출력 후 줄바꿈
        }
                                                                                            //
        // 현재 위치에 퀸을 놓아도 되는지 확인하는 유망함수
        private static boolean isSafe(int row, int col) {
            // 현재 행 이전의 모든 행을 검사
            for (int i = 0; i < row; ++i) {
                // 1. 같은 열에 퀸이 있는지 확인
                if (board[i] == col) {
                    return false; // 같은 열에 퀸이 있으면 false 반환
                }
                // 2. 같은 대각선에 퀸이 있는지 확인
                if (Math.abs(board[i] - col) == Math.abs(i - row)) {
                    return false; // 같은 대각선에 퀸이 있으면 false 반환
                }
            }
            return true; // 어떤 충돌도 없으면 true 반환
        }
                                                                                            //
        // N Queen 문제를 해결하기 위한 재귀 함수
        private static void solveNQueens(int row, int[] solutions) {
            // 모든 행에 퀸을 배치한 경우 (기저 조건)
            if (row == N) {
                // 해결책을 찾았으므로 해결책 수 증가
                solutions[0]++;
                // 현재 보드 상태를 출력
                printBoard();
                return; // 함수 종료
            }
                                                                                            //
            // 현재 행의 모든 열에 대해 반복
            for (int col = 0; col < N; ++col) {
                // 현재 위치에 퀸을 놓을 수 있는지 확인
                if (isSafe(row, col)) {
                    board[row] = col; // 현재 행의 열에 퀸을 놓음
                    solveNQueens(row + 1, solutions); // 다음 행에 대해 재귀 호출
                    // 퀸을 제거할 필요 없음, 다음 반복에서 덮어쓰기 때문에
                }
            }
        }
                                                                                            //
        public static void main(String[] args) {
            int[] solutions = {0}; // 해결책 수를 저장할 변수
                                                                                            //
            solveNQueens(0, solutions); // 첫 번째 행부터 시작
                                                                                            //
            System.out.println("총 해결책 수: " + solutions[0]); // 총 해결책 수 출력
        }
    }
```

>## <span style='color:#1E90FF'>피로도 문제 풀이</span>
- <a href='https://school.programmers.co.kr/learn/courses/30/lessons/87946' target='_blank' style='color:red'>피로도</a>

>## <span style='color:#1E90FF'>N-Queen 문제 풀이</span>
- <a href='https://school.programmers.co.kr/learn/courses/30/lessons/12952' target='_blank' style='color:red'>N-Queen</a>

>## <span style='color:#1E90FF'>양궁 대회 문제 풀이</span>
- <a href='https://school.programmers.co.kr/learn/courses/30/lessons/92342' target='_blank' style='color:red'>양궁 대회</a>