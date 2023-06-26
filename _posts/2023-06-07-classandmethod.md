---
layout: single
title:  "클래스와 메소드"
author_profiel : false
---


## class
 - 자바의 가장 작은 단위
 - 객체의 상태를 나타내는 필드와 객체의 행위를 나타내는 메소드로 구성된다.
 - java를 실행 시 클래스는 JAM 메모리의 클래스 영역(Class Area)에 로드된다.
 
 # class 구조
1. 필드
    - 클래스에 포함된 변수를 의미한다. 즉, 클래스 안, 메소드 밖에 선언된 변수이다.
    - 필드에서 다루는 변수는 클래스 변수와 인스턴스 변수이다.(이 두 변수는 static 키워드를 통해 구분할 수 있다.)

    |변수|선언위치|생성시기(메모리할당시기)|
    |-------|------|--------|
    |클래스변수|클래스영역|클래스가 메모리에 올라갈때|
    |인스턴수변수|클래스영역|인스턴스가 생성될 때|
    |지역변수|클래스 이외의 영역(메소드,생성자)|변수 선언문이 수행되었을때|


    * 클래스 변수 : 필드(즉, 클래스 안 메소드 밖) 내에 static 키워드와 함께 선언된 변수
    * 인스턴스 변수 : 필드 내에서 선언된 변수(static 키워드 없음)
    * 지역 변수 : 메소드 내에 포함된 모든 변수
2. 생성자
    - 객체가 실제로 생설될 때 초기화 역할을 담당한다.
3. 메소드
    - 객체의 동작에 해당하느 실행 블록이다.

 ```java
 public class DoorLockManager {
    //필드
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


# method
- 어떤 값을 주고 결과를 넘겨주는 것

# method 선언

접근제어자 리턴타입(자료형 또는 void) 메소드명(매개변수) {
    실행할 코드 작성;
    return; // 리턴타입이 void 일 경우 return 없음
}

```java
public boolean checkPassword(String password) {
    // 중간 내용
}
```

- checkPassword()라는 것은 "메소드 이름" 이 된다. 이 메소드를 부를때에는 "checkPassword 메소드"라고 부른다.
- password라는 것은 "매개변수(parameter)" 라고 부르며, 이 매개변수는 없어도 되고, 몇개가 오더라도 상관없다. 
- boolean이라는 것은 "리턴타입(return type)" 이라고 브른다. boolean이라는 것은 "참(true)"과 "거짓(false)"이라는 값만을 가지는 "기본 자료형"이라는 것 중 하나이다. 
 

