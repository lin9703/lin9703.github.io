---
layout: post
title: "의존성 주입(Dependency Injection)"
author: "Lin"
tags: Android
---

<br>

## Dependency Injection 용어 
- Dependency: 두 클래스가 상호의존적일 때 발생하는 매우 일반적인 상황 
    - 클래스 A가 클래스 B를 사용할 때 종속적이라고 한다.
    - 이때 클래스 A를 클라이언트, 클래스 B를 서비스라고 한다.
    - 그러나, 이런 관점은 상대적이라 문맥을 잘 파악해야 한다.
    - 문맥에 따라 어떤 클래스는 클라이언트이며 서비스이다. 
    
- 클라이언트가 서비스를 사용할 때, **서비스의 참조를 얻어야 한다.**
    - 참조를 얻는 방법
        1. 서비스의 인스턴스화
        2. Static 메소드 호출  
        3. Static global variable에 접근 
        4. `Receive references from "outside"`
        
        -> 1~3은 기본적으로 정적 인스턴스화이다. (active resolution of dependencies) <br>
        -> 클라이언트는 의존성을 해결하기 위해 서비스의 reference를 active하게 얻는다. <br>
        
        -> 반면에 4번은 수동적이다. <br>
        -> 종속성에 대한 reference가 외부에서 주입된다. <br>
        -> 이것이 의존성 주입 용어의 유래이다. <br>
        -> `Dependency Injection: providing services to clients from "outside"` 
        

<br>

## Dependency Injection의 기본 기법 
- 외부에서 서비스를 주입하는 세 가지 방법 (외부로부터 클라이언트에게 서비스를 제공하는 세 가지 옵션)
    1. Constructor Injection
    2. Method Injection
    3. Field Injection (Property in Kotlin)

- 의존성 주입을 통한 서비스 제공 
```Java
// 1. Constructor Injection
// 미리 초기화된 서비스의 인스턴스 필요
class Client(private val service1: Service1) {  
    
    // 2. Method Injection
    private var service2: Service2? = null
    
    // 3. Field Injection (property in Kotlin)
    // Kotlin에서는 대부분 Property Injection을 사용한다. 
    // public이므로 이 클라이언트에서 외부 엔티티는 레퍼런스를 확보 가능하고,
    // service stream에 대한 다른 유효한 레퍼런스와 함께 속성을 할당 가능하다.  
    lateinit var service3: Service3

    fun setService2(service2: Service2) {
        this.service2 = service2    
    }
}
```
1번과 2번은 자바에서 자주 사용되나, 코틀린에서는 자주 사용되지 않는다. <br>
자바의 Field injection과 비슷한 Property injection을 코틀린에서 사용할 수 있다. 

<br>

### 장단점 
#### 1. Constructor Injection
- 장점
    - Simple
    - 생성자가 내부 의존성을 반영
    - 주입된 서비스를 finalized 할 수 있다. (자바에서 final 키워드, 코틀린에서 val)
    - 단위 테스트에서 시험하기 쉽다. 

- 단점
    - None

#### 2. Method Injection
- 장점
    - 메소드가 의존성 반영 (메소드 객체를 리뷰할 수 있으면 즉시 종속성 이해 가능)
    - It can happen after construction (또 다른 서비스를 주입하고 싶을 때 생성자 주입은 인스턴스화 시간에 일어나기 때문에 불가능하다.)
- 단점
    - 생성자 주입보다 명시적이지 않다.
    - ordering requirements를 암시 (temporal coupling)
       > temporal coupling: 메서드 A는 언제나 반드시 메서드 B보다 먼저 호출해야 한다. <br>
        -> 대규모 시스템에서 매우 지저분해진다. (nonpoint or exception or silent malfunction 발생)                                   
    
#### 3. Field Injection (Property in Kotlin)
- 장점
    - It can happen after construction 
- 단점 
    - 메소드 주입의 모든 단점들 (non-explicit, temporal coupling)

#### 결론
생성자 주입을 쓰는 게 가장 좋지만 사용 불가능한 경우가 있다.
1. 클라이언트가 인스턴스화가 될 때, 서비스는 사용할 수 없는 경우 (ex: MyBleDeice for MyBleManager)
2. 클라이언트를 인스턴스화 하지 않는 경우 (ex: Activity)
3. 프레임워크가 생성자를 제한하는 경우 (ex: Fragment)

