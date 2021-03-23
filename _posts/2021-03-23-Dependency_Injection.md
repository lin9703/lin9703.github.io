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

