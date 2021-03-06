---
layout: post
title: "추상 클래스와 인터페이스"
author: "Lin"
tags: JAVA
---
### CS Study Day 6 - Part6

## 추상 클래스란?

- 추상 클래스는 미완성된 클래스이다.
- 미완성된 클래스는 미완성된 메소드인 추상 메소드를 포함하고 있다.
- 추상 클래스는 혼자로는 클래스의 역할을 다 못하지만, 새로운 클래스를 작성하는 데 있어 **그 바탕이 되는 부모 클래스로서의 중요한 의미**를 갖는다. 왜냐하면 클래스를 작성함에 있어서 어느정도 작성된 상태에서 시작할 수 있기 때문이다. 

<br>

## 인터페이스란?

- 인터페이스는 인터페이스를 구현하는 모든 클래스에 대해 특정한 메소드가 반드시 존재하도록 강제한다.
- 인터페이스의 목적은 구현 객체가 같은 동작을 한다는 것을 보장하는 것이다.
- 일종의 추상 클래스다. 하지만 추상 클래스보다 추상화 정도가 높아서 추상 메소드 이외의 일반 메소드나 멤버 변수를 구성원으로 가질 수 없다. 오직 추상 메소드와 상수만 멤버로 가질 수 있으며, 그 외의 요소는 허용하지 않는다.

<br>

## 추상 클래스와 인터페이스의 차이점

- 인터페이스
  - 클래스가 아니며, 클래스와 관련이 없다.
  - 추상 메소드와 상수만을 멤버로 가진다.
  - 한 개의 클래스가 여러 인터페이스를 구현할 수 있다. (다중 구현 가능.)
  - Java 8부터 default 메소드가 추가되었다. 
    - default 키워드가 붙은 메소드는 구현할 수 있으며(일반 메소드처럼), 자식 클래스에서는 이를 오버라이딩할 수 있다.
    - 인터페이스가 변경되면 이를 구현하는 모든 클래스들이 해당 메소드를 다시 구현해야하는 번거로운 문제가 있었다. 이런 문제를 해결하기 위하여 인터페이스에 메소드를 구현할 수 있도록 변경되었다.
  - Java 8부터 static 메소드가 추가되었다.
    - 인터페이스에 static 메소드를 선언 가능하게 함으로써, 간단한 기능을 가지는 유틸리티성 인터페이스를 만들 수 있게 되었다. 
  - 목적 : 구현 객체의 같은 동작을 보장하기 위해 사용한다.
- 추상 클래스
  - 클래스이며, 클래스와 관련이 있다. (주로 베이스 클래스로 사용)
  - 추상 메소드 및 일반 메소드와 멤버도 포함할 수 있다.
  - 한 개의 클래스가 여러 개의 클래스를 상속받을 수 없다. (다중 상속 불가능.)
  - 상속을 받아 기능을 확장시키는 데 목적이 있다.
  - 목적 : 기존의 클래스에서 공통된 부분을 추상화하여 상속하는 클래스에게 구현을 강제화한다. 메소드의 동작은 구현하는 자식 클래스로 위임한다. 
  - **공유의 목적**.
