---
layout: single
title:  "Object"
author_profiel : false
---

자바에서는 기본적으로 아무런 상속을 받지 않으면, java.lang.Object 클래스를 상속한다. 따라서 모든 자바 클래스의 부모인 java.lang.Ojbect 클래스이다.

# Object 클래스는 상속받는 이유
Object 클래스에 있는 메소드들을 통해서 클래스의 기본적인 행동을 정의할 수 있기 때문이다.

## Object 클래스에서 제공하는 메소드 종류
1. 객체를 처리하기 위한 메소드
- 자바에서 메소드를 표현할때에는 보통 아래 정리된 표와 같이 "접근제어자 리턴타입 메소드이름(매개변수)" 순으로 나열한다.

|메소드|설명|
|------|-------------|
|protected Object clone()|객체의 복사본을 만들어 리턴한다.|
|public boolean equals(Object obj)|현재 객체와 매개변수로 넘겨받은 객체가 같은지 확인한다. 같으면 true, 다르면 false를 리틴한다.|
|protected void finlize()|현재 객체가 더이상 쓸모가 없어졌을 때 가비지 컬렉션에 의해서 이 메소드가 호출된다.|
|public Class<?> getClass|현재 객체의 Class 클래스의 객체를 리턴한다.|
|public int hashCode()|객체에 대한 해시코드(16진수로 제공하는 객체의 메모리 주소) 값을 리턴한다.|
|public String toString()|객체를 문자열로 표현하는 값을 리턴한다.|

2. 쓰레드를 위한 메소드 

|메소드|설명|
|------|----------|
|public void notify()|이 객체의 모니터에 대기하고 있는 단일 쓰레드를 깨운다.|
|public void notifyAll()|이 객체의 모니터에 대기하고 있는 모든 쓰레드를 깨운다.|
|pulbic void wait()|다른 쓰레드가 현재 객체애 대한 notify()메소드나 notifyAll()메소드를 호출할 때까지 현재 쓰레드가 대기하고 있도록한다.|
|public void wait(long timeout)|wait()메소드와 동일한 기능을 제공하며, 매개변수에 지정한 시간만큼만 대기한다. 시간을 넘어 섰을때에는 현재쓰레드는 다시 깨어난다.|
|public void wait(long timeout, int nanos)|wait()메소드와 동일한 기능을 제공하며, wait(timeout)에서 밀리초 단위의 대기시간을 기다린다면, 이 메소든느 보다 자세한 밀리초+나노초(1/1,000,000,000초)만큼 대기한다.|

## toStirng()

## equals()
equals() 메소드는 두 객체가 동일한지 검사하기 위해 사용되며, 이는 동일성일 비교하는 것이다.즉, 두 객 체가 가리키는 곳이 동일한 메모리 주소일 경우에만 동일한 객체가 된다. 

```java
package equals_sample;

public class MemberDTO {
	public String name;
	
	public MemberDTO(String name) {
		this.name= name;
	}
}
```

```java
package equals_sample;

public class Equals {
	public static void main(String[] args) {
		Equals thisObject = new Equals();
		thisObject.equalsMethod();
	}
	
	MemberDTO obj1 = new MemberDTO("Sang");
    MemberDTO obj2 = new MemberDTO("Sang");
    MemberDTO obj3 = obj1;
    String a= "bin";
    String b = new String("bin");
    String c = "bin";
    
    System.out.println(obj1.equals(obj2)); // false 출력
    System.out.println(obj1.equals(obj3)); // true 출력
    System.out.println(a == b); // false 출력
    System.out.println(a == c); // true 출력
	}
}
```

위 소스와 같이 두 객체의 주소값이 달라 equals() 메소드로 비교했을 시 false가 나오게 된다. Overridng 하지 않은 equals() 메소드 즉, Object 클래스에 정의된 equals() 메소드는 아래 소스와 같다.

```java
public boolean equals(Object obj) {
        return (this == obj);
    }
```
== 연산자를 통해 비교하면 주소값이 같지 않으므로 두 객체는 동일하지 않다고 판단하여 false를 출력한다. 그러므로 두 객체를 비교할때는 equals()메소드를 Override 하여 재정의 해야된다. 단 equals() 메소드를 override 할때는 다섯가지 조건을 만족해야된다.
    - 재귀(reflexvie) : null이 아닌 x라는 객체의 x.equals(x) 결과는 항상 true 여야만한다.
    - 대칭(symmetric) : null이 아닌 모든 참조 값 x,y에 대해 x.equals(y)가 true면, y.equals(x)도 true 다.
    - 타동적(transitive) : null아닌 모든 참조값 x,y,z에 대해 x.equals(y)가 true고, y.equals(z)도 true면, x.equals(z) true 다.
    - 일단(consistent) : null아닌 x,y에 대해 x.equals(y)를 반복해서 호출하면 항상 true를 반환하거나 항상 false를 반환한다. 
    - null과의 비교 : null이 아닌 x라는 객체의 x.equals(null) 결과는 항상 false여야만 한다.

```java
@Override
public boolean equals(Object obj) {
    if (this == obj) { // 주소가 같으므로 당연히 true
        return true;
    }
    if (obj == null) { // obj가 null 이므로 당연히 false
        return false;
    }
    if (getClass() != obj.getClass()) { // 클래스 종유가 다르므로 false
        return false;
    }
    MemberDTO other = (MemberDTO) obj; // 같은 클래스이므로 형변환 실행

    if(name == null) {
        if(other.name != null) return false; // 비교 대상의 name이 null이 아니면 false
    } else if (!name.equals(other.name)) return false; // 두개의 name 값이 다르면 false
    
    return true;
}
```
위 소스와 같이 equals() 메소드를 override 할때에는 hashCode() 메소드도 같이 override 해야만 한다. 왜냐하면 equals() 메소드를 override 해서 객체가 서로 같다고 이야기할 수는 있겠지만, 그 값이 같다고 해서 그 객체의 주소 값이 같지는 않기 때문이다. 다시 말하면, equals() 메소드의 결과가 true 인데도 불구하고 , hashCode() 메소드의 값은 다르게 된다. 따라서 hashCode() 메소드도 object 클래스에서 제공하는 그대로 사용하면 안되고, 아래와 같이 사용해야 된다.

```java
@Override
	public int hashCode() {
		return Objects.hash(name);
	}
```

## hashCode()
hashCode() 메소드는 객체의 메모리 주소를 16진수로 리턴한다. 만약 어떤 두개의 객체가 서로 동일하다면, hashCode() 값은 무조건 동일해야만 한다. 따라서 equals() 메소드를 oerride 하면, hashCode() 메소드도 overried해서 동일한 결과가 나오도록 만들어야한다.