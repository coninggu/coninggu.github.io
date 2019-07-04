---
categories:
- 디자인패턴
tags:
- 디자인패턴
---

디자인 패턴 중 보그(borg) 패턴에 대해 알아보자.  

## 기본개념
보그 패턴은 monostate pattern이라고도 불린다. 싱글턴 패턴과 매우 유사하지만 싱글턴 패턴은 하나의 인스턴스만 갖는 대신에 보그 패턴은 여러개의 인스턴스에서 하나의 상태(state)를 공유한다는게 차이점이다. 즉, 하나의 인스턴스를 공유하는게 아니고 하나의 상태(state)를 공유하는 것이다.  

## 구현
python3:  
{% highlight python %}
class Borg:
    _shared_state = {}
 
    def __init__(self):
        self.__dict__ = self._shared_state
 
 
a = Borg()
b = Borg()
 
print(a is b)  # False
a.site = 'dolgonet'
print(b.site)  # dolgonet
{% endhighlight %}

일반적으로 파이썬의 인스턴스에는 __dict__이라는 속성이 있고,  모든 인스턴스에는 자신만의 __dict__을 가지고 있다.  
코드에서는 의도적으로 __dict__에 클래스 변수인 _shared_state를 할당하고, 이렇게 함으로써 모든 인스턴스는 하나의 상태(state)를 공유하게 되는 것이다.

## 참고자료
- [Python Design Pattern](http://www.acornpub.co.kr/book/python-design-patterns){:target="_blank"}
