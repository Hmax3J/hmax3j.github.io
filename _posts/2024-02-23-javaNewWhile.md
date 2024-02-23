---
title: "JAVA 개선된 Switch문"
date: 2024-02-24 12:00:00 AM +09:00
categories: [JAVA, Syntax_controlStatements]
---
***

>## <span style='color:#1E90FF'>JAVA 제어문</span>
JAVA 공부를 하던 중 Switch문이 새로 나왔다고 한다. <br>
무려 JDK14에서 도입 되었다고 하는데 필자는 지금 알았다... <br>
기존에 썻던 Switch문은 뭔가 직관성은 있었지만 불편했다. <br>
하지만 JDK14에서 개선된 Switch문은 확실히 차이가 있어 글을 남기고자 한다. <br>
기존의 Switch문은 아래의 코드와 같다.

```java
public static void main(String[] args) {
        String grade = "B";
        String result;

        switch (grade) {
            case "A":
                result = "탁월한 성과입니다!";
                break;
            case "B":
                result = "좋은 성과입니다!";
                break;
            case "C":
                result = "준수한 성과입니다!";
                break;
            case "D":
                result = "향상이 필요합니다!";
                break;
            case "F":
                result = "불합격입니다.";
                break;
            default:
                result = "잘못된 학점입니다.";
        }
        System.out.println(result);
}
```

> 딱 보아도 뭔가 복잡한 듯 하다. 하지만 아래의 JDK14에서 개선된 Switch문을 살펴보자.
```java
public static void main(String[] args) {
        String grade = "B";
        String result = switch (grade) {
            case "A" -> "탁월한 성과입니다!";
            case "B" -> "좋은 성과입니다!";
            case "C" -> "준수한 성과입니다!";
            case "D" -> "향상이 필요합니다!";
            case "F" -> "불합격입니다.";
            default -> "잘못된 학점입니다.";
        };
        System.out.println(result);
}
```
라인 수만 보아도 확실하게 코드 수가 줄었고 result =, break 를 계속 안써도 되니까 가독성도 좋아졌다. <br>
영한님 자바 강의를 듣던 중 알게 되었고, 앞으로 Switch문을 쓰게 된다면 새로운 Switch문을 적용하려고 한다. <br>
앞으로도 공부를 하다가 몰랐던 부분, 필요한 부분 등을 기록하려고 한다. 모두들 뽜이팅 !