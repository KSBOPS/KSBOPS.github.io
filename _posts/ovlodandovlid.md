---
layout: single
title:  "overloading vs overriding"
author_profiel : false
---

## overloading
- 하나의 클래스에 같은 이름의 메소드를 여러개 정의하는 것을 의미한다.
- 하나의 메소드 이름으로 여러기능을 구현할 수 있다.
- 메소도 이름이 같아야 한다.
- 매개변수의 개수,타입, 순서가 달라야한다.
- 매개 변수는 같고 리턴타입이 다른 경우는 오버로딩이 성립되지 않는다.
- 리턴타입은 오버로딩을 구현하는데 아무런 영향이 없다.

## overloading 대표적인 예
 - overloading의 가장 대표적인 예는 printSteam 클래스의 println()이다. 아래의 코드처럼 어떤 종류의 매개변수를 지정하더라도 출력할 수 있게 10개의 오버로딩된 메소드를 정해놓고 있다. 그래서 매개변수에 어떤 인자를 지정하더라도 출력할 수 있다.

 ```java
 void println();
 void println(boolean x);
 void println(char x);
 void println(char[] x);
 void println(double x);
 void println(float x);
 void println(int x);
 void println(long x);
 void println(Object x);
 void println(String x);
 ```

## overloading 사용하는 이유
 - 같은 기능을 하는 메소드를 하나의 이름으로 사용할 수 있기 때문
 - 메소드 이름을 절약할 수 있기 때문

# overloading 코드 예시
```java
package overloading_sample;

public class overloadingSample {
	public static void main(String[] args) {
		Member member = new Member();
		member.test();
		member.test(2);
		member.test(2,3);
		member.test("테스트");
		member.test(2+"테스트");
		
	} 
}

class Member {
	void test() {
		System.out.println("매개변수 없음");
	}
	void test(int a) {
		System.out.println(a);
	}
	
	int test(int a, int b) {
		System.out.println(a+b);
		return a+b;
	}
	void test (String a) {
		System.out.println(a);
	}
	
	String test (int a, String b) {
		System.out.println(a+b);
		return a+b;
	}

	//매개변수가 같은 int 타입의 메소드가 있어서 오버로딩이 성립되지 않고 에러난다.
	double test (int a, int b) {
		System.out.println(a+b);
		return a+b;
	}
}
```

## overriding
 - 상속받은 부모 클래스의 메소드를 재정의하여 사용하는 것을 의미한다.
 - 부모 메소드의 리턴타입, 메소드 이름, 매개변수 타입 및 갯수가 모두 동일해야만 한다.
 - 부모 클래스의 메소드보다 접근 제어자를 더 좁은 범위로 변경할 수 없습니다

 ## overriding 사용하는 이유
 - 같은 기능을 구현한 자식클래스에서 동일한 메소드를 사용함으로써 코드의 복장성과 일관성을 제공할 수 있다.
 - 상속 받은 메소드를 자식클래스에서 다른기능으로 사용하고자 하는 경우가 생기기 때문(코드 재사용성)

# overriding 코드 예시
```java
package overloading_sample;

public class overriding_sample {
	public static void main(String[] args) {
		Child child = new Child();
		child.pnt();
	}
}

//부모 클래스 생성
class Parent{
	
	public void pnt() {
		System.out.println("pnt - parentOverriding");
	}
}

//자식 클래스 상속
class Child extends Parent{
	
	public void pnt() {
		System.out.println("cld - cldOverriding");
	}
}
```


## 정리
오버로딩은 한 클래스 내에서 여러개의 같은 이름의 메소드를 정의한 것을 의미하며, 동일한 기능을 하는 메소드를 하나의 이름으로 처리할 수 있는 장점이 있다.
오버라이딩은 부모로부터 받은 메소도의 로직을 자식 클래스에서 다시 재정의해서 사용하는 것을 의미한다. 즉, 부모 클래스의 로직을 자식클래스에서 재정의하여 다른 기능으로 사용할 수 있다는 장점이 있다.

