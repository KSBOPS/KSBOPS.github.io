---
layout: single
title:  "VO와 DTO"
author_profiel : false
---

## VO(Value Object)
  - 값 자체를 나타내는 객체
  - 변하지 않는 데이터 객체
  - read-only 속성으로 getter만 가능

## VO를 사용하는 이유
  * 객체 안에 제약사항을 추가할 수 있다.
   
  * 생성될 인스턴스가 정해져 있는 경우 미리 인스턴스를 생성해놓고 캐싱하여 성능을 높일 수 있다.

  * Entity의 원시값들을 VO로 포장하면 Entity가 지나치게 거대해지는 것을 막을 수 있어서 테이블 관점이 아닌 객체 지향적인 관점으로 프로그래밍할 수 있다.
       

## DTO(DATA Transfer Object)
 - 데이터 전송 객체
 - Layer(Controller, View, Business Layer)간 데이터 교환하는 객체
 - 로직을 갖고 있지 않는 순수한 데이터 객체, getter/setter 메소드만 가지고 있다. 

```java
package dto_sample;

public class dtoSample {
	private String name;
	private int age;
	
	public dtoSample(String name, int age) {
		this.age= age;
		this.name = name; 
	}

	public String getName() {
		return name;
	}
	
	public void setName(String name) {
		this.name = name;
	}
	
	public int getAge() {
		return age;
	}
	
	public void setAge(int age) {
		this.age = age;
	}
}
```

## DTO를 사용하는 이유
  * 객체를 표현하는 계층와 저장하는 계층의 역할을 분리하기 위해서

  * Entity 객체를 그대로 사용하면 프로그래머 의도와 다르게 데이터가 변질될 수 있기 때문이다.

  * 클라이언트와 통신하는 DTO 클래스는 요구사항에 따라 자주 변경됩니다. 즉, 어떠한 특정 값이 추가 되거나 없을 수도 있기 때문이다.

## DTO 와 VO 차이
- 데이터 전송 목적 / 값 표현 목적
- 가변(setter 존재) 또는 불변(setter 비존재) / 불변
- 로직 포함 불가능 / 로직 포함 가능
- 읽고 쓰기 가능 / 읽기만 가능
- 필드값이 같아서 다른 객체 / 필드값이 같으면 같은 객체
