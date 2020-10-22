---
layout: post
title: "추상 메소드와 추상 클래스"
author: "Lin"
tags: JAVA
---

## 추상 메소드
- 자식 클래스에서 반드시 오버라이딩해야만 사용할 수 있는 메소드
{% highlight java %}
abstract 반환타입 메소드이름();
{% endhighlight %}
<br>

## 추상 클래스 
- 하나 이상의 추상 메소드를 포함하는 클래스<br/>
- 객체 지향 프로그래밍에서 중요한 특징이 다형성을 가지는 메소드의 집합을 정의할 수 있도록 한다.<br/>
즉, 반드시 사용되어야 하는 메소를 추상 클래스에 추상 메소드로 선언하면, 이 클래스를 상속받는 모든 클래스에서는 이 추상 메소드를 반드시 재정의해야 한다. 

{% highlight java %}
abstract class 클래스이름 {
    ... 
    abstract 반환타입 메소드이름();   
    ...
} 
{% endhighlight %}

- 사용 이유: 추상 메소드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메소드를 구현하도록 하기 위함이다.<br/>
추상 메소드가 포함된 추상 클래스를 상속받은 모든 자식 클래스는 추상 메소드를 구현해야만 인스턴스를 생성할 수 있다.