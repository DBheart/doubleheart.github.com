
1. 개요
> GOF패턴에는 총 23개의 패턴이 있다. GOF를 만든 4명(?)은 왜 3개로 나누었을까? 처음에 나는 GOF패턴끼리 어떻게 다른가를 많이 찾았다. 서로 비슷비슷하다보니 잘 외워지지도 않고 말이다. 이번에 다시 살펴보기 시작하였다. 무엇이든 저자의 의도가 중요하다. 하지만 나의 의도도 중요하다. 몬 소리냐고? 저자의 의도가 몬지 모르겠으니 나의 의도대로 한번 살펴보겠다는 것이다. 아직까지 다른 사람들이 본 GOF패턴을 보야야 겠지만 내가 생각한것 부터 정리하고 보도록 하겠다. 

패턴을 가르는 기본 토대는 실생활과 어떤 연관점이 있는가로 두었다. 어떤 책을 보니 건축도 하나의 유기체라고 한다. 그렇다면 실생활을 기초로 만들어지는 프로그래밍도 하나의 유기체라고 생각된다. 

2. 패턴끼리 상관관계
> 우선은 생성패턴은 모든 패턴의 기초가 되는 것이라고 생각한다. 
> 각 패턴에도 기본이 되는 패턴이 있는데, 생성패턴에서 제일 기본적인 것은 Factory Method이다. 그리고 구조패턴에서는 Adapter, Bridge, Composite가 기본이 된다. 행동패턴에서는 Strategy가 기본적인 패턴이 되겠다. 

3. GOF 직접 코딩하고 다시정리를 계속 하고 있다. 하면서 느낀것은 이미 우리의 코드에 녹아나 있다는 것이다.

# 생성패턴 5
Factory Method
Abstract Factory
Builder
Prototype
Singleton
# 구조패턴 7
Adapter
Facade
Decorator
Bridge
Composite
Flyweight
Proxy
# 행동패턴 11
Strategy
Template Method
Iterator
State
Mediator
Memento
Command
Visitor
Chain of Responsibility
Observer
Interpreter

---

* [코드참조](http://www.w3sdesign.com/GoF_Design_Patterns_Reference0100.pdf)
* [UML 참조](http://vincehuston.org/dp/all_uml.html)

분류로 나누어본 디자인패턴

	1. 인터페이스 사용
		- Strategy는 로직 분리
			- State는 스위칭
			- Bridge는 로직의 분할
		- Template Method는 
			- 인터페이스가 아닌 추상클래스를 사용하는 방법
			- 로직을 뼈대를 만들고 상세로직은 다른 클래스에서 진행하는 방식으로 abstract으로 구현해야한다.	
	2. recursive 반복
		- 반복을 위해서는 List가 필요하다. 객체를 모은다.
		- Composite는 트리구조
			- Interpreter는 List에 담겨 있는 데이터의 검색/분석으로 많이 쓰인다.
			- Decorator은 값을 추가하기 위한 것이고
			- Chain Of Responseibility는 분업, 처리할수 있으면 하지만 아니면 다음것으로 넘기는 것
		- Flyweight는 Composite와 비슷하게 객체를 담지만, pool구조
	3. ETC(로직 분할의 처리)
		- Mediator은 비슷한 행동에 대해서 처리방식을 하나의 클래스에 모아두는 방식이다. 
		- Observer는 등록된 객체를 한꺼번에 업데이트 하는 방식이다.
		- Visitor는 유형별로 처리방식 정의, 방문객에 대한 처리로직을 모두 정의해 놓는다.		
	4. 대신 처리(클래스 재사용)
		- Facade는 기존에 있는것들을 하나의 메서드에서 불러와서 처리하도록 한다.
		- Adapter는 기존것의 인터페이스명(or param) 변경
		- Proxy는 우선은 내가 처리할수 있는곳까지 처리하고 최종적으로는 예전객체를 호출해서 한다.
	5. UI
		- Command는 이벤트에 대한 처리방식
		- Memento는 복구방법
		- Iterator로 반복할때 임시저장을 위해서 Memonto를 쓸수도 있다고 이야기 한다.
			> UML은 이해가 잘 안된다.
	6. 생성패턴
		- Builder는 복합객체만들기, 요소별로 정의해서 조립하여서 내놓는 것
		- AbstractFactory은 제품군별로 객체만드는 것을 정의해 놓은 것
		- FactoryMethod는 다른 클래스의 메서드에서 객체를 생성하도록 하는 것
		- ProtoType은 복제이다. 현재 있는것을 복제하여서 하는것. 디자인패턴에 있는 uml은 잘 이해가 안된다.
		- Singleton은 객체의 공유를 위해서 유일하게 만드는 방식이다.
	7. 패턴 공부의 유용성	
		- 객체에서 사용할 일반적인 방법을 정의
		- UML에 대해서 예시를 알수가 있다.
		- 언어에 대한 패턴 기준을 정할수 있다.
		- 설계할때 아 이건 이런 패턴을 쓰자고 해서 공부했는데.. 이건모 그렇게 쓸정도는 아닌것 같다. 구현을 위해서 쓰는것이랄까나?

---

그들이 나누었을 대화내용 추정을 해보자. 나름 재미나는데.. 일관성이 없는것 같기도 하다.
