---
categories:
- 디자인패턴
tags:
- 디자인패턴
---

디자인 패턴중에서 싱글턴(Singleton) 패턴에 대해서 알아보자.    

## 기본개념
싱글턴 패턴은 오래전부터 많이 알려지고 사용된 디자인 패턴중에 하나로 하나의 클래스에 인스턴스를 하나만 만들어야하는 경우 사용되는 패턴이다.최초 생성 이후에 호출되는 생성자는 최초 인스턴스를 리턴한다.

싱글턴은 다음과 같은 상황에 사용된다.  
1. 공유자원(shared resource)에 대한 동시접근(concorrenct access)을 제어할 필요가 있는 경우.
2. 여러 시스템에서 하나의 자원에 접근하는 지점이 필요한 경우.
3. 유일객체(unique object)가 필요한 경우.

일반적으로 싱글턴이 사용되는 예는 다음과 같다.
1. logging class.
2. print spooler.
3. DBCP(Dabasebase Connection Pool).
4. File Manager.
5. 전역 상태를 담고 있는 읽기 전용 싱글턴.

## 구현
python3:  
{% highlight python %}
class Singleton:
    def __new__(cls, *args, **kwargs):
        if not hasattr(cls, 'instance'):
            cls.instance = super(Singleton, cls).__new__(cls)
        return cls.instance
 
a = Singleton()
b = Singleton()
print(a) #<__main__.Singleton object at 0x10d4d5278>
print(b) #<__main__.Singleton object at 0x10d4d5278>
{% endhighlight %}

아래는 위키피디아에서 작성되어 있는 예제 코드이다.  
{% highlight python %}
class Singleton(type):
    def __init__(cls, name, bases, dict):
        super(Singleton, cls).__init__(name, bases, dict)
        cls.instance = None
 
    def __call__(cls, *args, **kw):
        if cls.instance is None:
            cls.instance = super(Singleton, cls).__call__(*args, **kw)
        
        return cls.instance
 
class MyClass(object):
    __metaclass__ = Singleton
 
print MyClass()
print MyClass()
{% endhighlight %}

Descorator 사용:
{% highlight python %}
def singleton(cls):
    instance = []
    def getinstance():
        if not len(instance):
            instance.append(cls())
        return instance[0]
    return getinstance
 
@singleton
class MyClass:
    ...
{% endhighlight %}
