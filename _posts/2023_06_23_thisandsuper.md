---
layout: single
title:  "this and spuer"
author_profiel : false
published: true
---

## this
- 자기 자신을 지징하는 키워드
- 현재 클래스 필드에 존재하는 인스턴스변수를 지정할때 사용한다.
- 현재 클래스의 인스턴스를 가리킨다.
- 주로 생성자와 메소드의 매개변수 이름이 필드와 비슷하거나 같은 경우, 헷갈리지 않도록, 인스턴스 멤버인 필드임을 명시하고자 할때 사용된다.


## this()
- 같은 클래스에서 생성자가 다른 생성자를 호출할 때 사용한다.
- 생성자 코드에서만 사용할 수 있다.
- 생성자 코드 안에서 사용될 때 첫번째 문장으로 다른코드보다 가장 윗줄에 위치해야 한다.

```java
public class Book{
    String title;
    int price;

    public Book() {             // 기본생성자
        this("미입력", -1);
    }
    
    public Book(String title) { // 매개변수 1개 가진 생성자
        this(title, 0);
    }
    public Book(String title, int price) { //매개변수 2개 가진 생성사
        this.title = title;
        this.price = price;
    }

    public void showPrice() {
        System.out.println(title + "의 가격은 " + price + "원입니다.");
    }
}

public class bookMain {
	public static void main(String [] args) {
		Book b1 = new Book();
		Book b2 = new Book("비매품");
		Book b3 = new Book("국어책", 30000);
		
		b1.showPrice();
		b2.showPrice();
		b3.showPrice();
	}

} 

미입력의 가격은 -1원입니다.
비매품의 가격은 0원입니다.
국어책의 가격은 30000원입니다.
```
위 코드에서는 총 3개의 생성자를 만들었고, 기본 생성자에 this("미입력" , -1)와 this(title, 0) 은 매개변수가 2개인 생성자를 호출한다. 매개변수가 2개인 생성자 안에 this.title 은
클래스의 맴버변수를 지칭한다.

## super
- 자신이 상속받은 부모 클래스에 대한 레퍼런스 변수로, 부모 클래스의 맴버에 접근할 때 사용한다.

## super()
- 자식 클래스의 생성자에서 부모클래스의 생성자를 호출하기 위해서 사용한다.

```java
public class superEx {
	public static void main(String [] args) {
		Child ch = new Child();
		ch.show();
	}
}

class Parent {
	int x = 10;
	int y = 5;
	
	Parent() {
		System.out.println("부모 기본 생성자");
	}
	
	Parent(int x, int y) {
		this.x = x;
		this.y = y;
	}
	
	public void show() {
		System.out.println("x = " + x + ", y = " + y);
	}
}

class Child extends Parent {
	int x = 20;
	
	Child() {
	}
	
	Child(int x , int y) {
		super(x,y);
	}
	
	public void show() {
		super.show();
		System.out.println("x= " + x);
		System.out.println("this.x= " + this.x);
		System.out.println("super.x= " + super.x);
	}
}

부모 기본 생성자
x = 10, y = 5
x= 20
this.x= 20
super.x= 10

```

부모 생성자를 먼저 호출 한 후, 자식 생성자를 호출한다. 부모 클래스에 생성자 여러개 있어도 기본적으로 기본생성자를 먼저 실행되고 기본생성자가 존재하지 않을 경우 컴파일 에러가 발생한다.(즉, 매개변수가 있는 생성자가 있을 경우 기본 생성자는 자동으로 생기지 않는다.)
