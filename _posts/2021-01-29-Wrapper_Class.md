---
layout: post
title: "Wrapper Class"
author: "Lin"
tags: JAVA
---
### CS Study Day 12 - Part6

<br>

## Wrapper Class 
기본 자료형(Primitive data type)에 대한 클래스 표현을 의미 <br>
Integer, Float, Boolean 등 

<br>

### 사용 용도 
- 객체로 저장해야 할 경우
- 매개변수로 객체가 요구될 경우 (Collection에서 Generic을 사용하기 위해서 Wrapping한 형태 사용)
- null 값을 반환하는 경우 return type으로 지정 

<br>

### 특징 
- `Immutable`: 값에 대한 변경은 불가하고 새로운 객체의 할당이나 참조만 가능
- JDK 1.5부터 `AutoBoxing`과 `AutoUnBoxing`을 제공
    - AutoBoxing:  기본 자료형 -> Wrapper Class
    - AutoUnBoxing : Wrapper Class -> 기본 자료형
- 비교할 때 `.intValue()` 메소드를 통해 해당 Wrapper class의 값을 가져와 비교

