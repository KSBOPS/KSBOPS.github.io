---
layout: single
title:  "Enum class"
author_profiel : false
---

## Enum class
 - Enumeration 앞 글자로 열거형이라고 부르며, 서로 연관된 상수들의 집합을 의미한다.
 - jdk 1.5 버전부터 사용할 수 있다.
 - final static과 같은 방식으로 상수를 정의한다.
 - enum 클래스의 부모는 무조건 java.leng.enum 클래스 이어야 한다.
 - enum을 extends를 이용하여 선언할 수 없다.
 - enum 클래스는 switch 문에서 사용하는 것이 효과적이다.

# enum class 예제

 ```java
 package enumclass_sample;

//enum 클래스는 일반클래스와 다르게 컴파일할 때 생성자를 자동으로 만들어준다.
public enum OverTimValues {
	THREE_HOUR,
	FIVE_HOUR,
	WEEKEND_FOUR_HOUR,
	WEEKEND_EIGHT_HOUR;
}
```

```java
package enumclass_sample;
public class OverTimeManager {
	public int getOverTimeAmount(OverTimValues value) {
		int amount = 0;
		System.out.println(value);
		switch(value) {
			case THREE_HOUR :
				amount = 18000;
				break;
			case FIVE_HOUR : 
				amount = 30000;
				break;
			case WEEKEND_FOUR_HOUR :
				amount = 40000;
				break;
			case WEEKEND_EIGHT_HOUR:
				amount = 60000;
				break;
		}
		return amount;
	}
	public static void main(String[] args) {
		OverTimeManager manager = new OverTimeManager();
		int myAmount = manager.getOverTimeAmount(OverTimValues.THREE_HOUR);
		//위 소스를 풀어서 쓰면 아래와 같다.
		/* 
		OverTimValues value = OverTimValues.THREE_HOUR; //value라는 변수는 OverTimValues라는 enum 클래스의 객체
		int myAmount = manager.getOverTimeAmount(value); 
		*/
		System.out.println(myAmount);
	}
}

THREE_HOUR
18000

 ```

 enum 클래스는 생서자를 만들 수 있지만, 생성자를 통하여 객체를 생성할 수 없다.
 enum 상수 값을 지정하여 사용이 가능하며, 값을 동적으로 할당하는 것은 불가능하다.
 위 코드를 아래와 같이 만들 수 있다.
 
 ```java
 package enumclass_sample;

public enum OverTimValues2 {
	THREE_HOUR(18000),
	FIVE_HOUR(30000),
	WEEKEND_FOUR_HOUR(40000),
	WEEKEND_EIGHT_HOUR(60000);
	private final int amount;
	
	
	//생성자, public으로 되어 있지 않음. 
	//enum 클래스 생성자는 아무것도 명시하지 않는 packge-private과 private만 접근 제어자로 사용할 수 있다.
	//public 과 protected를 생성자로 사용해서는 안됨.
	OverTimValues2(int amount){ 
		this.amount= amount;
	}
	
	//enum 클래스의 변수로 선언한 amount 값을 리턴하기 위해
	public int getAmount() {
		return amount;
	}
}

```

```java
package enumclass_sample;

public class OverTimeManager2 {
	public static void main(String[] args) {
		OverTimValues2 value2 = OverTimValues2.FIVE_HOUR;
		System.out.println(value2);
		System.out.println(value2.getAmount());
		
		OverTimValues2 value3 = OverTimValues2.THREE_HOUR;
		System.out.println(value2.compareTo(value3)); //compareTo 메소드 사용
	}
}

FIVE_HOUR 
30000
1

 ```


## Enum class 생성자

|접근제어자|메소드|설명|
|--------|----------|-----------------|
|protected|Enum(String name, int ordinal)| 컴파일러에서 자동을 호출되도록 해놓은 생성자다. 하지만, 개발자가 이 생성자를 호출 할 수 없다.|

여기서 name은 enum 상수의 이름이다. ordinal은 enum의 순서이며, 상수가 선언된 순서대로 0부터 증가한다.

## Enum class에서 선언되어 있는 메소드
1. Static Methods

|메소드|설명|
|-----|-------------|
|valueOf(String arg)|String 값을 enum에서 가져온다. 값이 없으면 Exception 발생|
|valueOf(Class<T> class, String arg)|첮번째 매개변수로는 클래스 타입의 enum을, 두번째 매개변수로는 상수의 이름을 넙겨주면 된다.|
|values()|enum의 요소들을 순서대로 enum 타입의 배열로 리턴한다.|

2. Static 아닌 Methods

|메소드|설명|
|-----|-------------|
|name()| String 값으로 상수의 이름을 리턴한다.|
|ordinal()|상수의 순서를 리턴한다.|
|compareTo(E e)|매개 변수 enum 타입과의 순서(ordinal) 차이를 리턴한다.|
|equals(Object o)|지정된 객체가 이 enum 정수와 같을 경우, true를 반환한다.|


## Enum을 쓰는 이유
- 코드가 단순해지고, 가독성이 좋아진다.
- 인스턴스의 생성과 상속을 방지하여 상수값의 안정성이 보장된다.
- enum을 이용해 새로운 상수들의 타입을 정의하므로써 정의한 타입 외 타입을 가진 데이터값을 컴파일 시 체크 할 수 있다.
- enum이라는 키워드를 통해 구현의 의도를 파악할 수 있다.

