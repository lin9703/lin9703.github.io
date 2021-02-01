---
layout: post
title: "Generic"
author: "Lin"
tags: JAVA
---
### CS Study Day 13 - Part6

<br>

## Generic
- Java에서 무언가를 담는 Container를 만들 때, 담을 객체의 Type을 `Dynamic`하게 저장할 수 있는 방법 
- Java 1.5부터 도입되어 Class Code 작성 시점에 임의의(<T>) 타입을 사용하도록 하고, 
그 Class를 사용하는 Code에서 <T> 대신 실제 사용하는 Type(<String>)을 사용
- `컴파일 과정`에서 타입 체크 <br>
    - 객체의 타입 안전성 ↑ / 형변환의 번거로움 ↓ / 코드 간결
- 예를 들어, Collection에 특정 객체만 추가될 수 있도록 지정 <br>
    - Collection 내부에 들어온 값이 내가 원하는 값인지 별도의 로직 처리 구현할 필요 X
- API를 설계할 때 보다 명확한 의사전달 가능 
 

