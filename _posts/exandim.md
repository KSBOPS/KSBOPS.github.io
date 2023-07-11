---
layout: single
title:  "extends 와 implements 차이"
author_profiel : false
---

## extends
 - 부모클래스가 가진 메소드나 변수를 자식클래스가 물려 받아서 사용 할 수 있게 한다.
 - 다중 상속이 불가능하다
 - 여러 자식 클래스에 상속이 가능하다.
 - extends 키워드 뒤에는 하나의 부모클래스만 와야 된다.
 - class가 class, interface가 interface를 상속받을 때 extends 키워드 사용한다.
 - 부모 클래스의 private 접근 제한을 갖는 필드 및 메소드는 자식이 물려받을 수 없다.
 - 부모와 자식 클래스가 서로 다른 패키지에 있다면 부모의 default 접근 제한을 갖는 필드 및 메소드는 물려 받을 수 없다.
 
## extends 를 하는 이유
이미 만들어져 있는 클래스를 재사용할 수 있기 때문에 효율적이고 중복된 코드가 줄어들어 코드가 간결해진다. 그리고 공통적인 기능을 부모 클래스에 추가해주면 상속받은 여러개의 자식 클래스에서 사용이 가능한다.
다시말해, 유지보수가 쉬워지고 확장성이 용이해지고 재사용이 가능해지고 코드가 간결해지며 시간을 단축할 수 있다.

# extends 코드 예시
```java
package extends_semple;

public class extendsSample {
	public static void main (String[] args){
		Child A = new Child();
		A.name = "테스트";
		A.getName();
		A.getSpeak();
	}
} 

//부모 클래스
class Parent {
	potected String name;
	
	public void getName(){
		System.out.println("이름 : "+ name);
	}
}

//부모 클래스 상속받는 자식 클래스
class Child extends Parent{
	public void getSpeak(){
		System.out.println(name + " 말한다." );
	}
}
```

## implements
 - interface 구현
 - 부모 인터페이스의 메소드나 변수를 선언만하고 기능적 구현은 하지않고,자식클래스에서 선언만 된 메소드를 @Override로 구현 해주는 것을 말한다. 
 - 다중 상속이 가능하다.
 - class가 interface를 사용할때 implements 키워드 사용한다.
 - 설계 목적으로 구현 가능하다.
 - implements 한 클래스는 implements의 내용을 다 사용해야 한다.


# implements 코드 예시
```java
package implements_sample;

public interface atest{
	public void atest1();
	public void atest2();
	
}

public interface btest{
	public void btest1();
	
}

class cClass implements atest, btest {

	@Override
	public void btest1() {
		System.out.println("atest1");
		
	}

	@Override
	public void atest1() {
		System.out.println("atest2");
		
	}

	@Override
	public void atest2() {
		System.out.println("abest1");
		
	}

}

public class implementsSample {
	public static void main(String[] args) {
		cClass c = new cClass();
		c.atest1();
		c.atest2();
		c.btest1();
	}
}
```

## 정리
extends는 클래스는 확정한다는 의미로 다중상속이 불가능하고, 클래스가 클래스를 인터페이스가 인터페이스를 상속받을 때 사용한다.
implements는 인터페이스를 구현하는 것으로, 다중상속이 가능하며, 클래스가 인터페이스를 사용할 때 구현된다. 또한 implements 한 클래스는 interface의 내용을 다 사용해야된다.