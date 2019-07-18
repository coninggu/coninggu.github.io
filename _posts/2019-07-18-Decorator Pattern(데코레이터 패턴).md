---
categories:
- 디자인패턴
tags:
- 디자인패턴
---

디자인 패턴 중에서 데코레이터(Decorator) 에 대해서 알아보자. 

## 기본개념
데코레이터 패턴은 어떤 한 객체에 기존 동작은 변경하지 않고 새로운 기능을 다이나믹하게 장식해 주는 것을 말한다.
그리고 추가한 새로운 기능이 모든 서브 클래스에 영향을 끼치는 것이 아니고 특정 객체에만 끼친다.

## 구현
간단한 예제 코드를 통해 다시 살펴보자. 아래 예제는 카페 모카에 샷과 휘핑을 추가한 코드이다.  

{% highlight python %}
# python3
class Order:
    def __init__(self, name):
        self._name = name
 
    def cost(self):
        return 4000
 

class Shot(Order):
    def __init__(self, coffee):
        self._coffee = coffee
  
    def cost(self):
        return self._coffee.cost() + 500
 

class Whip(Order):
    def __init__(self, coffee):
        self._coffee = coffee
 
    def cost(self):
        return self._coffee.cost() + 200
 

if __name__ == '__main__':
    o1 = Order('Mocha')
    o2 = Whip(Shot(o1)) # [1]
 
    print(o1.cost())  # 4000
    print(o2.cost())  # 4700 
{% endhighlight %}
1. 코드를 해석하면 Order 클래스는 Shot, Whip의 Base 클래스인 슈퍼 클래스이고 name을 인자로 받아서 self.name에 대입하여 생성하고 cost 메소드는 기본 가격인 4000을 반환한다.
2. Shot 클래스는 Order 클래스를 계승하고 Order를 참조 할 수 있는 coffee를 아규먼트로 받아 인스턴스 변수인 self._coffee에 대입한다. cost 메소드는 self._coffee.cost()를 호출하여 반환된 4000에 500을 더한다. Whip 클래스도 Shot 클래스와 동일하다. 
3. 최종적으로 4700이 출력된다.

## 장점
1. 데코레이터 패턴을 사용하면 런타임시에 특정 객체에 대해서만 새로운 기능을 확장할 수 있다.
2. 서브클래스의 대안이다. 서브클래스는 컴파일시에 기능이 추가되고 클래스의 모든 인스턴스에 영향을 주지만 데코레이터 패턴은 런타임시 특정 객체에 대해서만 기능을 확장 할 수 있다.


## 단점
1. 데코레이터 패턴을 많이 사용하거나 여러개의 데코레이터로 래핑하게 되면 복잡해진다.
2. 데코레이터 패턴으로 새로운 기능이 확장될수록 가독성이 떨어진다.


## 사용시기
1. 모든 서브 클래스에 영향을 주지 않고 특정 객체에만 기능을 확장하고 싶은 경우

## OCP
데코레이터 패턴은 객체지향 5대 원리 중 하나인 OCP(Open/Close Principle)에 해당한다. 

버틀란트 메이어(Bertrand Meyer)박사가 1998년 객체지향 소프트웨어 설계 라는 책에서 정의한 내용으로 소프트웨어의 구성요소(컴포넌트, 클래스, 모듈, 함수)는 확장에는 열려있고, 변경에는 닫혀있어야 한다는 원리입니다. 이것은 변경을 위한 비용은 가능한 줄이고 확장을 위한 비용은 가능한 극대화 해야 한다는 의미로, 요구사항의 변경이나 추가사항이 발생하더라도, 기존 구성요소는 수정이 일어나지 말아야 하며, 기존 구성요소를 쉽게 확장해서 재사용할 수 있어야 한다는 뜻입니다. 로버트 C. 마틴은 OCP는 관리가능하고 재사용 가능한 코드를 만드는 기반이며, OCP를 가능케 하는 중요 메커니즘은 추상화와 다형성이라고 설명하고 있습니다. OCP는 객체지향의 장점을 극대화하는 아주 중요한 원리라 할 수 있습니다.  
[출처:http://www.nextree.co.kr/p6960/](http://www.nextree.co.kr/p6960/){:target="_blank"}

## 참고자료
- [http://www.geeksforgeeks.org/the-decorator-pattern-set-2-introduction-and-design/](http://www.geeksforgeeks.org/the-decorator-pattern-set-2-introduction-and-design/){:target="_blank"}




	
