
1. 개요
> GOF패턴에는 총 23개의 패턴이 있다. GOF를 만든 4명(?)은 왜 3개로 나누었을까? 처음에 나는 GOF패턴끼리 어떻게 다른가를 많이 찾았다. 서로 비슷비슷하다보니 잘 외워지지도 않고 말이다. 이번에 다시 살펴보기 시작하였다. 무엇이든 저자의 의도가 중요하다. 하지만 나의 의도도 중요하다. 몬 소리냐고? 저자의 의도가 몬지 모르겠으니 나의 의도대로 한번 살펴보겠다는 것이다. 아직까지 다른 사람들이 본 GOF패턴을 보야야 겠지만 내가 생각한것 부터 정리하고 보도록 하겠다. 

패턴을 가르는 기본 토대는 실생활과 어떤 연관점이 있는가로 두었다. 어떤 책을 보니 건축도 하나의 유기체라고 한다. 그렇다면 실생활을 기초로 만들어지는 프로그래밍도 하나의 유기체라고 생각된다. 

2. 패턴끼리 상관관계
> 우선은 생성패턴은 모든 패턴의 기초가 되는 것이라고 생각한다. 
> 각 패턴에도 기본이 되는 패턴이 있는데, 생성패턴에서 제일 기본적인 것은 Factory Method이다. 그리고 구조패턴에서는 Adapter, Bridge, Composite가 기본이 된다. 행동패턴에서는 Strategy가 기본적인 패턴이 되겠다. 

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