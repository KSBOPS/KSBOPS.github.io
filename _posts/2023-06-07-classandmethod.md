---
layout: single
title:  "class and method"
author_profiel : false
---

# method
- 어떤 값을 주고 결과를 넘겨주는 것

```java
public boolean checkPassword(String password) {
    // 중간 내용
}
```

- checkPassword()라는 것은 "메소드 이름" 이 된다. 이 메소드를 부를때에는 "checkPassword 메소드"라고 부른다.
- password라는 것은 "매개변수(parameter)" 라고 부르며, 이 매개변수는 없어도 되고, 몇개가 오더라도 상관없다. 
- boolean이라는 것은 "리턴타입(return type)" 이라고 브른다. boolean이라는 것은 "참(true)"과 "거짓(false)"이라는 값만을 가지는 "기본 자료형"이라는 것 중 하나이다. 
 

# class
 - 자바의 가장 작은 단위
 
 ```java
 public class DoorLockManager {
    String currentPassword;
    public boolean checkPassword(Stirng password) {
        // 중간 생략
    }
    // 그 외 메소드 생략
 }

 ```
- DoorLockManager 이라는 것은 "클래스 이름(class name)" 이다. 
- 클래스 안에는 메소드가 위치하는데, 하나의 클래스 안에는 0개 이상의 여러 메소드가 존재할 수 있다.
- 클래스는 상태(state)와 행동(behavior)이 있어야만 한다.
- 상태(state)는 클래스 안에, 메소드 밖에 정의한다.
- 행동(behavior)은 메소드로 정의한다.
- currentPassword 같은 것을 변수(variable)이라고 하며, 클래스의 특성을 결정짓는 "상태"에 해당한다.
- 반드시 "상태"와 "행동"이 있어야 하는 것은 아니다.
