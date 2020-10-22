---
layout: post
title: "Kotlin 생성자"
author: "Lin"
tags: Kotlin
---
   
## 1. 주 생성자 (Primary Constructor)
생성자 파라미터를 지정하고 그 생성자 파라미터에 의해 초기화되는 Property를 정의하는 두 가지 목적으로 쓰인다. 
클래스는 하나의 주 생성자와 다수의 부 생성자를 가질 수 있다.

<details>
<summary style="font-Weight : bold; font-size : 10px;">about Property</summary>
<div markdown="1" style="font-size: 13px;">
<br>
객체의 구성 요소 : 속성(Property)와 기능(Function)의 집합
 - 속성(Property): 멤버 변수(member variable), 특성(attribute), 필드(field), 상태(state)
 - 기능(Function): 메소드(method), 행위(behavior), 함수(function)

</div>
</details>

<br>
{% highlight java %}
class JWTUtil(JWTEncoded: String)
{% endhighlight %} 

주 생성자는 클래스 선언과 함께 정의된다. <br>
위의 경우 'constructor' 키워드가 생략되었으나, 어노테이션이나 접근 제어자를 가지면 생략할 수 없다.

<br>

## 1.1 init으로 초기화
코틀린의 주 생성자에는 어떠한 코드도 추가될 수 없기에 초기화를 하기 위해서 init 블록을 지원한다.
init 블록에는 클래스의 객체가 만들어질 때 실행될 초기화 코드가 들어간다.

{% highlight java %}
class JWTUtil(JWTEncoded: String) {
    val jwt: JWT
    
    init {
        jwt = JWT(JWTEncoded)
    }
}
{% endhighlight %}
 
<br>

## 1.2 부 생성자 (Secondary Constructor)
생성자가 여러개 필요할 때는 부 생성자를 생성하여 사용한다. constructor 키워드를 사용하며 생략 불가능하다. 

{% highlight java %}
class TextView: View {
    constructor(context: Context): this(context, null) {
        ....
    }
    
    constructor(context: Context, attr: AttributeSet): super(context, attr) {
        ....
    }
}
{% endhighlight %}

클래스의 주생성자가 존재한다면, 부 생성자는 무조건 주 생성자에게 직간접적으로 생성을 위임해야 한다.
클래스의 주생성자가 없다면, 모든 부 생성자들은 상위 클래스를 초과하거나, 다른 생성자에게 이를 위임해야 한다. 


<br>[참고 블로그1](https://velog.io/@conatuseus/Kotlin-%EC%83%9D%EC%84%B1%EC%9E%90-%EB%BF%8C%EC%8B%9C%EA%B8%B0)
<br>[참고 블로그2](https://tourspace.tistory.com/107)
<br>[참고 블로그3](https://zerogdev.blogspot.com/2019/06/constructor.html)