---
title: "[코딩테스트 합격자 되기 스터디] 3주차 - 해시 (7.21 ~ 7.27)"
date: 2024-07-27 01:35:00 AM +09:00
categories: [Algorithm, Study]
tags: [java, algorithm, study]
---
***

>## <span style='color:#1E90FF'>코딩테스트 합격자 되기 스터디 3주차</span>
강의 보기 -> 해당되는 부분 책 다시 읽기 -> 블로그 정리 <br>
강의는 C++로 되어 있지만 개념적인 내용이라 언어 상관 없이 보고 코드는 각 언어에 맞게 바꾸면 된다. <br>

>## <span style='color:#1E90FF'>참고 강의 및 책</span>
인프런 : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 인프런 강의 링크</a> <br>
Youtube : <a href='https://inf.run/t92e1' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬, C+_+ 저자님 Youtube 링크</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000210881884' target='_blank' style='color:red'>코딩테스트 합격자 되기 파이썬 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213087020' target='_blank' style='color:red'>코딩테스트 합격자 되기 C++ 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000213641007' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바스크립트 편</a> <br>
종이책 : <a href='https://product.kyobobook.co.kr/detail/S000212576322' target='_blank' style='color:red'>코딩테스트 합격자 되기 자바 편</a> <br>

>## <span style='color:#1E90FF'>해시</span>
- 해시함수를 사용해서 변환한 값을 인덱스로 삼아 키-값을 저장해 빠른 데이터를 탐색하는 자료구조

>## <span style='color:#1E90FF'>해시 함수</span>
- 임의의 키를 해시테이블의 인덱스로 변경해주는 함수 <br>
- 해시 테이블의 크기가 N이라면 해시 함수는 0 ~ (N - 1) 사이 값 <br>
- 충돌을 최소화 할수록 좋은 해시 함수 <br>
- 나눗셈법
    - 값을 해시 테이블(N)의 크기로 나눈 나머지를 해시값으로 사용하는 방법
    - h(x) = x mod k (x는 키, k는 소수)
    - k로 나눈 나머지는 0 ~ (k - 1) 이므로 해시 테이블의 크기는 k
    - k가 소수인 이유는 충돌을 줄이기 위함(소수가 아니면 k주기로 해시 값 반복)
    - 7 % 2 -> 2로 나누면 0 또는 1로 반복, 충돌이 엄청 많이 발생
- 곱셈법
    - 소수를 활용하지 않고 황금비를 곱하는 방식
    - h(x) = (((x * A) mod 1) * m)
- 문자열 해싱
    - 문자열의 아스키 코드 값을 활용한 해싱
    - hash(s) = (s[0] + s[1] * p + s[2] * p^2 + ... + s[n-1] * p^n-1) mod m

>## <span style='color:#1E90FF'>해시 충돌</span>
- 서로 다른키에 대해 해시 함수 결과 값이 같을 경우 충돌 발생 <br>
- 체이닝, 개방 주소법이 충돌을 처리하는 대표적인 방법
- 체이닝
    - 충돌 발생 시, 해당 버킷에 링크드리스트로 데이터를 연결
    - 특정 버킷에 데이터가 N개인 경우, 원하는 값을 찾는데 O(N)이 걸릴 수 있음
- 개방 주소법 - 선형 탐사
    - 충돌 발생 시, 다른 빈 버킷을 찾아 충돌 값을 삽입
    - 최대한 기존 테이블을 사용하자는 방식(메모리를 아낄 수 있음)
    - h(k,i) = (h(k) + i) mod m
    - k는 키, i는 충돌 시 이동할 버킷 수, m은 버킷 사이즈
- 개방 주소법 - 이중 해싱
    - 해시 함수를 2개 사용(경우에 따라 N개 까지 확장)
    - 기존에 i를 더했던 선형 탐사와 다르게 2번째 해시함수에 i를 곱하는 방식도 가능
    - 이 때 클러스터를 줄이기 위해 m을 제곱수나 소수로 함
    - h(k,i) = (h1(k) + i * h2(k)) mod m
    - k는 키, i는 임의의 수, h1은 첫 번째 해시 함수, h2는 두 번째 해시 함수, m은 테이블 크기

>## <span style='color:#1E90FF'>해시 활용</span>
- 키, 값 쌍으로 연관된 데이터가 존재하며, 해당 값에 대한 접근이 빈번한 경우
    - 사전(단어를 검색)이나 연락처(이름을 검색)
- 중복되지 않는 키를 사용하는 경우
    - 학번이나 집 주소(중복되지 않음)

>## <span style='color:#1E90FF'>해시를 사용하지 말아야 하는 경우</span>
- 특정 키에 여러 가지 값을 매칭해야 하는 경우
    - 키 1개에 2개의 값이 생기지 않고 값이 갱신되어 저장

>## <span style='color:#1E90FF'>오픈 채팅방 문제 풀이</span>
- <a href='https://school.programmers.co.kr/learn/courses/30/lessons/42888' target='_blank' style='color:red'>오픈 채팅방</a> <br>
```java
public String[] solution(String[] record) {
    HashMap<String, String> map = new HashMap<>();
    List<String[]> list = new ArrayList<>();
    for (String value : record) {
        String[] str = value.split(" ");
        if (str[0].equals("Enter") || str[0].equals("Change")) {
            map.put(str[1], str[2]);
        }
        if (str[0].equals("Enter")) {
            list.add(new String[] {str[1], "님이 들어왔습니다."});
        } else if (str[0].equals("Leave")) {
            list.add(new String[] {str[1], "님이 나갔습니다."});
        }
    }
    String[] result = new String[list.size()];
    for (int i = 0; i < list.size(); i++) {
        String[] strValue = list.get(i);
        result[i] = map.get(strValue[0]) + strValue[1];
    }
    return result;
}
```
- 시간복잡도: O(N * M)

>## <span style='color:#1E90FF'>메뉴 리뉴얼 문제 풀이</span>
- <a href='https://school.programmers.co.kr/learn/courses/30/lessons/72411' target='_blank' style='color:red'>메뉴 리뉴얼</a> <br>
```java
private static HashMap<Integer, HashMap<String, Integer>> courseMap;
public String[] solution(String[] orders, int[] course) {
    courseMap = new HashMap<>();
    for (int i : course) {
        courseMap.put(i, new HashMap<>());
    }
    for (String order : orders) {
        char[] orderArray = order.toCharArray();
        Arrays.sort(orderArray);
        combinations(0, orderArray, "");
    }
    ArrayList<String> answer = new ArrayList<>();
    for (HashMap<String, Integer> count : courseMap.values()) {
        count.values()
             .stream()
             .max(Comparator.comparingInt(o -> o))
             .ifPresent(cnt -> count.entrySet()
                    .stream()
                    .filter(entry -> cnt.equals(entry.getValue()) && cnt > 1)
                    .forEach(entry -> answer.add(entry.getKey())));
    }
    Collections.sort(answer);
    return answer.toArray(new String[0]);
}
public static void combinations(int idx, char[] order, String result) {
    if (courseMap.containsKey(result.length())) {
        HashMap<String, Integer> map = courseMap.get(result.length());
        map.put(result, map.getOrDefault(result, 0) + 1);
    }
    for (int i = idx; i < order.length; i++) {
        combinations(i + 1, order, result + order[i]);
    }
}
```
- 못 풀었다... ↑ 다른 사람의 풀이 ↑ <br>
- 시간복잡도: O(N * 2^M)