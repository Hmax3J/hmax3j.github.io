---
title: "대표적인 메모리 관련 버그"
date: 2024-05-15 09:00:00 PM +09:00
categories: [ComputerScience, 컴퓨터구조]
tags: [cs, computer, science, architecture]
---
***

>## <span style='color:#1E90FF'>컴퓨터 구조</span>
컴퓨터 구조를 공부하면서 알게된 내용을 요약해서 작성해보자. <br>

>## <span style='color:#1E90FF'>지역 변수의 포인터 반환하기</span>
```
int* func()
{
    int a = 2;
    return &a;
}
void main()
{
    int* p = func();
    *p = 20;
}
```
- 지역 변수 a가 func 함수의 스택 프레임에 위치하며 func 함수의 실행이 끝나면 해당 스택 프레임도 없어진다. main 함수가 func 함수를 호출한 후 얻는 포인터는 이미 없는 변수를 가리키게 된다. <br>

>## <span style='color:#1E90FF'>포인터 연산의 잘못된 이해</span>
```
int sum(int* arr, int len)
{
    int sum = 0;
    for(int i = 0; i < len; i++>)
    {
        sum += *arr;
        arr += sizeof(int);
    }
    return sum;
}
```
- 포인터 연산에서 1을 더하는 것은 1바이트만큼 이동하는 것이 아니라 단위 한 개만큼 이동하는 것이다. <br>
- 단위 한 개는 포인터가 가리키는 데이터 형식의 크기에 해당한다. <br>
- 포인터가 가르키는 데이터 형식이 int 형일 때 포인터에 1을 더하는 것은 4바이트 만큼 이동하는 것이다. <br>

>## <span style='color:#1E90FF'>문제 있는 포인터 역참조</span>
```
int a;
scanf("%d", a);
```
- a 값이 코드 영역이나 기타 읽기 전용 영역을 가리키는 포인터 값으로 해석되면 운영 체제는 이 프로세스를 즉시 강제 종료 시킨다. 이것은 제일 좋은 상황이며, 문제를 찾는 것은 그리 어렵지 않다. <br>
- a 값이 스택 영역을 가리키는 포인터 값으로 해석되었다면 다른 함수의 스택 프레임이 파괴되었기 때문에 프로그램이 이제 무슨 짓을 할 지 알 수 없으며, 이런 버그는 원인을 찾기가 매우 어렵다. <br>

>## <span style='color:#1E90FF'>이미 해제된 메모리 참조하기</span>
```
void add()
{
    int* a = (int*)malloc(sizeof(int));
    ...
    free(a);
    int b = *a;
}
```
- 포인터 a가 가리키는 메모리 조각이 해제된 후 malloc으로 다시 할당하지 않았다면 a가 가리키는 값은 이전과 동일하다. <br>
- 포인터 a가 가리키는 메모리 조각이 이미 malloc로 할당되었다면 a가 가리키는 메모리는 이미 덮어쓰기가 되었을 수 있다. a를 역으로 참조하여 얻는 것은 이미 덮어쓰기가 된 데이터다. <br>

>## <span style='color:#1E90FF'>스택 넘침</span>
```
void buffer_overFlow()
{
    char buf[32];
    gets(buf);
    return;
}
```
- 모든 함수는 실행될 때 스택 영역에 자신만의 스택 프레임을 가진다. <br>

>## <span style='color:#1E90FF'>메모리 누수</span>
```
void memory_leek()
{
    int *p = (int *)malloc(sizeof(int));
    return ;
}
```
- 프로세스가 종료되기 전까지는 다시 해제할 방법이 없어 메모리 누수가 일어난다. <br>