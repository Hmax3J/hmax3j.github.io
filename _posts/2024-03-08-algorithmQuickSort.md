---
title: "Algorithm, Quick Sort, 퀵 정렬"
date: 2024-03-08 04:35:00 PM +09:00
categories: [Algorithm, QuickSort]
tags: [java, algorithm, sort, quicksort]
---
***

>## <span style='color:#1E90FF'>기록하자.</span>
3월 상반기 공채가 시작되었다. 코딩테스트 보는 곳이 많아 알고리즘에 대해 공부를 다시 시작했다. <br>
그리고 블로그도 만들었기에 퀵 정렬에 대해 공부한 내용을 기록하고자 한다. <br>
좋은 일은 모두 꿈에서 시작했다 라는 말도 있기에 간절하게 바라며 공부하고 <br>
준비를 잘해서 이번에는 내 차례가 되어 기회라는 녀석을 잡을 수 있길...

>## <span style='color:#1E90FF'>프로그래머스 K번째 수</span>
프로그래머스의 알고리즘 고득점 kit 카테고리의 정렬에서 <a href='https://school.programmers.co.kr/learn/courses/30/parts/12198' target='_blank' style='color:red'>K번째 수</a> 문제다. <br>
문제를 짧게 요약 하자면 배열이 주어지고 그 배열의 i부터 j까지 자르고 정렬한 후 k번째의 수를 구하는 문제다. <br>
여기서 i,j,k 는 2차원 배열로 주어진다. 이 입력을 가지고 문제를 풀어야 한다. <br>
처음 문제를 보고 아래 처럼 로직을 생각했다. <br>
- 2차원 배열 추출하기
    - 가장 밖에 있는 큰 배열 추출하기
    - 큰 배열안의 작은 배열 추출하기
- 추출한 값을 토대로 배열 자르기
    - 배열을 자른 후 정렬하기
- 정렬된 배열의 k번째 값 return 배열에 담기 <br>

>## <span style='color:#1E90FF'>구현 코드</span>
다음은 필자가 구현한 알고리즘이다.
```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int length = 0;
        int[] answer = new int[commands.length];
        int commandStart = 0;
        int k = 0;
        for(int i = 0; i < commands.length; i++) {
            length = commands[i][1] - commands[i][0] + 1;
            commandStart = commands[i][0] - 1;
            k = commands[i][2] - 1;
            int[] slicedArray = new int[length];
            for(int index = 0; index < length; index++) {
                slicedArray[index] = array[commandStart + index];
            }
            Arrays.sort(slicedArray);
            answer[i] = slicedArray[k];
        }
        return answer;
    }
}
```
이렇게 구현하고 제출하니 문제 당 0.4 ~ 0.6ms 정도의 속도가 나왔다. <br>
필자는 여기서 정렬할 때 Arrays.sort를 사용했다. 하지만 이것을 사용하고 나서 의문이 들었다. <br>
이것이 알고리즘 구현이 맞는가 ? 그냥 메서드 사용한 것 아닌가 라는 의문이 들어 한참 고민했다. <br>
고민끝에 이 부분을 퀵 정렬로 만들어보자고 생각해 퀵 정렬을 사용해서 다시 구현해 보았다.

>## <span style='color:#1E90FF'>퀵 정렬 구현 코드</span>
```java
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        for(int i = 0; i < commands.length; i++) {
            int length = commands[i][1] - commands[i][0] + 1;
            int start = commands[i][0] - 1;
            int end = commands[i][1] - 1;
            int k = commands[i][2] - 1;
            int[] slicedArray = new int[length];
            if(length == 1) {
                answer[i] = array[start];
                continue;
            }
            for(int j = 0; j < length; j++) {
                slicedArray[j] = array[start + j];
            }
            quickSort(slicedArray, 0, length - 1);
            answer[i] = slicedArray[k];
        }
        return answer;
    }
    public void quickSort(int[] array, int startIndex, int endIndex) {
        if(startIndex < endIndex) {
            int pivotIndex = partition(array, startIndex, endIndex);
            quickSort(array, startIndex, pivotIndex - 1);
            quickSort(array, pivotIndex + 1, endIndex);
        }
    }
    public int partition(int[] array, int startIndex, int endIndex) {
        int middleIndex = startIndex + (endIndex - startIndex) / 2;
        int temp = array[middleIndex];
        array[middleIndex] = array[endIndex];
        array[endIndex] = temp;
        int pivot = array[endIndex];
        int minIndex = startIndex - 1;
        for(int i = startIndex; i < endIndex; i++) {
            if(array[i] < pivot) {
                minIndex++;
                temp = array[minIndex];
                array[minIndex] = array[i];
                array[i] = temp;
            }
        }
        temp = array[minIndex + 1];
        array[minIndex + 1] = array[endIndex];
        array[endIndex] = temp;
        return minIndex + 1;
    }
}
```
퀵 정렬을 직접 구현하니 코드 수가 굉장히 많아지긴 했다... <br>
Arrays.sort는 1줄 쓰면 끝인데 직접 구현하니 몇 줄이 늘어났는지 모르겠다. <br>
물론 속도는 상당히 빨라졌다. 한 문제당 0.02 ~ 0.04 ms 로 나왔다. <br>


> 하지만 필자가 생각하기에 메서드를 사용하면 이게 알고리즘 구현이 맞는가 의문이 들기도 하고, <br>
코딩테스트에서 문제가 많은데 이걸 구현하면 다른 문제 풀 시간이 부족할 것 같았다. <br>
아직도 답을 내리지 못했다. 분명 직접 구현하는 것이 맞는데 알고리즘 구현에 익숙하지 못해, <br>
직접 구현한다면 시간이 오래 걸린다. 메서드를 사용하면 시간이 획기적으로 줄어든다. <br>
분명 사용할 수 있는 기능이니 사용하는 것이 맞지만 구현력을 보여줘야 하는 코딩테스트에서, <br>
이것이 맞는가 계속 의문이 들기도 하고 많이 혼란스러웠다. 결국, 이 문제를 해결하려면 메서드를 안써도, <br>
내가 빨리 구현하면 되겠다. 라고 결정을 내렸다. 그렇게 하려면 문제를 많이 풀어야 할 것 같다. <br>
코딩테스트 까지 남은 시간이 2주 정도 되는데 정말 최소한의 잠과 휴식시간을 제외하고, <br>
한 번 미친듯이 문제를 풀어 보려고 한다. 나이도 어린 편이 아니라 이제는 진짜 더욱 절실하게, 간절하게 <br>
준비를 해서 좋은 환경에서 좋은 사람들과 함께 일하며 성장하여 성취감을 느끼고 싶다. <br>
힘들때도 항상 그 생각을 하며 버텨야겠다.