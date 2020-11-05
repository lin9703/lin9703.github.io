---
layout: post
title: "Call by value와 Call By Reference (JAVA)"
author: "Lin"
tags: JAVA
---

메소드로 인자값을 넘기는 방법은 2가지가 있다.
<br>
## Call by value
값에 의한 호출
메소드 호출 시 사용되는 인자의 메모리에 저장된 _값_ 을 복사한다.<br>
이 방식으로 메소드 호출하면 메소드 내에서는 복사된 값으로 작업을 해 원래의 값을 변경하지 않는다.

## Call by reference
참조에 의한 호출<br>
메소드 호출 시 사용되는 인자 값의 메모리에 저장된 _주소_ 를 복사한다.<br>
메소드 내에서도 원래의 값에 접근이 가능하다.

<br>

---

<h3> 자바는 항상 Call by value이다.<br>
불행하게도, 객체를 전달할 때 Reference를 전달하는데 이것은 초보자들을 헷갈리게 한다.</h3>

[출처](https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value)

<br>

{% highlight java %}
public static void main(String[] args) {
    Dog aDog = new Dog("Max");
    Dog oldDog = aDog;

    // we pass the object to foo
    foo(aDog);
    // aDog variable is still pointing to the "Max" dog when foo(...) returns
    aDog.getName().equals("Max"); // true
    aDog.getName().equals("Fifi"); // false
    aDog == oldDog; // true
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // change d inside of foo() to point to a new Dog instance "Fifi"
    d = new Dog("Fifi");
    d.getName().equals("Fifi"); // true
}
{% endhighlight %}

객체 참조가 value에 의해 전달 된 것처럼 main의 aDog는 foo 함수의 Dog "Fifi"와 함께 변경되지 않는다.<br>
reference로 전달 된다면, foo를 호출 한 후 main에 있는 aDog.getName()은 "Fifi"를 반환 했을 것이다. 

<br>
{% highlight java %}
public static void main(String[] args) {
    Dog aDog = new Dog("Max");
    Dog oldDog = aDog;

    foo(aDog);
    // when foo(...) returns, the name of the dog has been changed to "Fifi"
    aDog.getName().equals("Fifi"); // true
    // but it is still the same dog:
    aDog == oldDog; // true
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // this changes the name of d to be "Fifi"
    d.setName("Fifi");
}
{% endhighlight %}

의 예에서, foo(aDog) 를 호출한 후에 aDog.getName()은 Fifi 가 된다. <br>
왜냐하면 객체의 이름은 foo 내부에서 setName('Fifi') 되었기 때문이다. <br>
foo가 d에서 수행하는 모든 연산은 모든 실질적인 목적을 위해 aDog에서 수행되지만, 변수 aDog 자체의 값을 변경할 수는 없다. 

<br>
<h3> 요약 </h3>
call by value로 전달된 것처럼 foo 내부에서의 변경(new Dog("Fifi"))는 적용되지 않는다.

하지만 setter 메소드를 이용한 aDog필드의 값은 변경이 가능하다. 이 때문에 사람들이 헷갈려한다. 

aDog 자체 reference를 바꾸는 것은 불가능하지만 setter 메소드를 이용한 aDog필드의 값은 변경이 가능하다. 

+ C에서 온 사람들은 "reference"는 "pointer"와 같다. C++에서 온 사람들은 C++에서의 의미와 같다. <br>
Java reference가 실제로 전달되는 것이 올바른지 여부는 "reference"가 의미하는 바에 달려 있다. 

<br>[참고 블로그1](https://hyoje420.tistory.com/6)
<br>[참고 블로그2](https://dublin-java.tistory.com/33)
