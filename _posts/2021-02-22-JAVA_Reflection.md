---
layout: post
title: "JAVA Reflection"
author: "Lin"
tags: JAVA 
---
### CS Study Day 18 - Part3

<br>

## Reflection
- 자바에서 이미 로딩이 완료된 클래스에서 또는 다른 클래스를 동적으로 로딩하여 구체적인 타입을 알지 못하더라도 생성자, 멤버 필드, 그리고 멤버 메소드를 사용할 수 있는 기법이다.
- 객체를 통해서 클래스의 패키지 정보, 접근 지정자, 부모 클래스, 어노테이션 등을 얻을 수 있다.
- 즉, 핵심은 컴파일 타임이 아니라 **런타임에 동적**으로 특정 클래스의 정보를 객체화하여 분석 및 추출해낼 수 있는 프로그래밍 기법이다.

<br>

### 사용 이유
- 실행 시간(Runtime)에 다른 클래스를 동적으로 로딩하여 접근할 필요가 있을 때
- 클래스와 멤버 필드 그리고 메소드 등에 관한 정보를 얻어야할 때
- 리플렉션 없이도 완성도 높은 코드를 구현할 수 있지만, 사용한다면 조금 더 유연한 코드를 만들 수 있다

<br>

#### 주의사항 
- 외부에 공개되지 않는 private 멤버도 Field.setAccessibile() 메소드를 통해 true로 지정하면 접근과 조작이 가능하기 때문에 주의해서 사용해야 한다.
- Reflection에는 동적으로 해석되는 유형이 포함되므로 특정 JVM 최적화를 수행할 수 없다. 
따라서 Reflection 작업이 비 Reflection 작업보다 성능이 떨어지며, 성능에 민감한 애플리케이션에서 자주 호출되는 코드엔 사용하지 않아야 한다.



<br>
[출처]

https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Java/%5BJava%5D%20Reflection.md