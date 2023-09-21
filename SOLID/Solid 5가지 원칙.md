>[!info] Solid
>- **S**RP(Single Responsibility Principle): 단일 책임 원칙
>-  **O**CP(Open Closed Priciple): 개방 폐쇄 원칙
>-  **L**SP(Listov Substitution Priciple): 리스코프 치환 원칙
>-  **I**SP(Interface Segregation Principle): 인터페이스 분리 원칙
>-  **D**IP(Dependency Inversion Principle): 의존 역전 원칙

## S: Single responsibility principle(SRP)
안녕하세요asdfasdfasdfasdfasdfdjdlrk\\어이가 없ㅓㅓ네
하이용ㅎㅎ
- 단일 책임 원칙은 **클래스(객체)는 단 하나의 책임만 가져야** 한다는 원칙
- 여기서 **'책임'** 이라는 의미는 하나의 '**기능 담당'으로 보면 된다
- 즉, **하나의 클래스는 하나의 기능 담당하여 하나의 책임을 수행**하는데 집중되도록 클래스를 따로따로 여러개 설계하라는 원칙이다.
-  최종적으로 단일 책임 원칙의 목적은 **프로그램의 유지보수 성을 높이기 위한** 설계 기법이다.


## O : 개방 폐쇄 원칙 - OCP (Open Closed Principle)
![[Pasted image 20230921154709.png]]

 - OCP 원칙은 클래스는 **'확장에 열려있어야 하며, 수정에는 닫혀있어야 한다'** 를 뜻한다.
 -  기능 추가 요청이 오면 **클래스를** **확장을 통해 손쉽게 구현**하면서, **확장에 따른 클래스 수정은 최소화** 하도록 프로그램을 작성해야 하는 설계 기법이다.
    - [ 확장에 열려있다 ] - 새로운 변경 사항이 발생했을 때 유연하게 코드를 추가함으로써 큰 힘을 들이지 않고 애플리케이션의 기능을 확장할 수 있음
    - [ 변경에 닫혀있다 ] - 새로운 변경 사항이 발생했을 때 객체를 직접적으로 수정을 제한함.


## 리스코프 치환 원칙 - LSP (Liskov Substitution Principle)
![[Pasted image 20230921153931.png]]
- LSP 원칙은 **서브 타입은 언제나 기반(부모) 타입으로 교체**할 수 있어야 한다는 원칙이다.
-  쉽게 말하면 LSP는 **다형성 원리를 이용하기 위한 원칙** 개념으로 보면 된다.

>[!faq] Tip!
>자바에선 대표적으로 Collection 인터페이스를 LSP의 예로 들수있다.  
>Collection 타입의 객체에서 자료형을 LinkedList에서 전혀 다른 자료형 HashSet으로 바꿔도 ~~add()~~ 메서드를 실행하는데 있어 원래 의도대로 작동되기 때문이다.  
  한마디로 다형성 이용을 위해 부모 타입으로 메서드를 실행해도 의도대로 실행되도록 구성을 해줘야 하는 원칙이라 이해하면 된다.

```` java
public void myData() {
	// Collection 인터페이스 타입으로 변수 선언
    Collection data = new LinkedList();
    data = new HashSet(); // 중간에 전혀 다른 자료형 클래스를 할당해도 호환됨
    
    modify(data); // 메소드 실행
}

public void modify(Collection data){
    list.add(1); // 인터페이스 구현 구조가 잘 잡혀있기 때문에 add 메소드 동작이 각기 자료형에 맞게 보장됨
    // ...
}
````
<<<<<<< HEAD



## 인터페이스 분리 원치 - ISP (Interface Segregation Principle)
![[Pasted image 20230921154852.png]]
=======
칙 - ISP (Interface Segregation Principle)

![[Pasted image 20230919150704.png]]
>>>>>>> origin/main
- ISP 원칙은 **인터페이스를 각각 사용에 맞게 끔 잘게 분리**해야한다는 설계 원칙이다.
- SRP 원칙이 **클래스의 단일 책임**을 강조한다면, ISP는 **인터페이스의 단일 책임**을 강조하는 것으로 보면 된다.  
- 즉, SRP 원칙의 목표는 클래스 분리를 통하여 이루어진다면, ISP 원칙은 인터페이스 분리를 통해 설계하는 원칙.  
- 다만 ISP 원칙의 주의해야 할점은 *한번 인터페이스를 분리하여 구성해놓고 나중에 무언가 수정사항이 생겨서 또 인터페이스들을 분리하는 행위* 를 가하지 말아야 한다.  
    (인터페이스는 한번 구성하였으면 웬만해선 변하면 안되는 정책 개념)

>[!tip]
>인터페이스는 제약 없이 자유롭게 다중 상속(구현) 이 가능하기  때문에, 분리할 수 있으면 분리하여 각 클래스 용도에 맞게 implements 하라는 설계 원칙이다.

## 의존 역전 원칙 - DIP (Dependency Inversion Principle)
![[Pasted image 20230921154905.png]]

- DIP 원칙은 어떤 Class를 참조해서 사용해야하는 상황이 생긴다면, 그 Class를 직접 참조하는 것이 아니라 그 **대상의 상위 요소(추상 클래스 or 인터페이스)로 참조**하라는 원칙
- 쉽게 이야기해서 구현 클래스에 의존하지 말고, **인터페이스에 의존**하라는 뜻
- 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는, 변화하기 어려운 것 거의 변화가 없는 것에 의존하라는 것
>[!tip]
>> 의존 역전 원칙의 지향점은 각 클래스간의 결합도(coupling)을 낮추는 것이다.



