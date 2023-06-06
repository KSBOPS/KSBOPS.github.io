---
layout: single
title:  "overloading vs overriding"
author_profiel : false
---

## overloading
오버로딩은 같은 이름의 메소드 여러개를 매개 변수 타입과 갯수를 다르게 정의한 것을 의미한다.


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
}
```

위 코드와 같이 test라는 같음 이름을 가진 다섯개의 메소드가 매개변수의 개수와 타입을 다르게 지정하여 작성한 것이다.

## overriding
오버라이딩은 상속 관계에 있는 부모 클래스에서 이미 정의된 메소드를 자식 클래스에서 동일한 메소드를 선언한 것을 의미한다.

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
위 코드와 같이 부모 부모 클래스에 있는 pnt() 메소드를 자식 클래스에서 pnt() 메소드로 재정의하여 사용하였다. 
(단, 리턴타입, 메소드 이름, 매개변수 타입 및 갯수가 모두 동일해야만 한다.)
또한 접근 제어자는 부모 클래스의 메소드보다 좁은 범위로 변경할 수 없다. 즉, 부모 클래스의 메소드의 접근제어자가 public으로 되어 있는데, 자식 클래스의 메소드가 pirvate으로 선언되어 있을 경우 에러가 발생한다.


## 정리
오버로딩은 한 클래스 내에서 여러개의 같은 이름의 메소드를 정의한 것을 의미하며, 동일한 기능을 하는 메소드를 하나의 이름으로 처리할 수 있는 장점이 있다.
오버라이딩은 부모로부터 받은 메소도의 로직을 자식 클래스에서 다시 재정의해서 사용하는 것을 의미한다. 즉, 부모 클래스의 로직을 자식클래스에서 재정의하여 다른 기능으로 사용할 수 있다는 장점이 있다.

