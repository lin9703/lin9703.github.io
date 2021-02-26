---
layout: post
title: "JAVA Reflection"
author: "Lin"
tags: JAVA 
---
### CS Study Day 19 - Part1

<br>

프로그램이 실행 중 어떤 원인에 의해서 오작동을 하거나 비정상적으로 종료되는 경우를 **프로그램 오류**라 하고, 프로그램 오류에는 에러(error)와 예외(exception) 두 가지로 구분할 수 있다.
 
- **Error** : 컴파일 시 문법적인 오류와 런타임 시 널포인트 참조와 같은 오류로 프로세스에 심각한 문제를 야기시켜 프로세스를 종료 시킬 수 있다. 

- **Exception** : 컴퓨터 시스템의 동작 도중 예기치 않았던 이상 상태가 발생하여 수행 중인 프로그램이 영향을 받는 것로 예를 들면, 연산 도중 넘침에 의해 발생한 끼어들기 등이 해당된다.
프로그래머가 적절히 코드를 작성해주면 비정상적인 종류를 막을 수 있다.

<br>

## Error (에러)
Error는 시스템 레벨에서 발생하여, 개발자가 어떻게 조치할 수 없는 수준을 의미한다.
- OutOfMemoryError : JVM에 설정된 메모리의 한계를 벗어난 상황일 때 발생한다. 
힙 사이즈가 부족하거나, 너무 많은 class를 로드할때, 가용가능한 swap이 없을때, 큰 메모리의 native 메소드가 호출될 때 등이 예시이. 
이를 해결하기 위해 dump 파일분석, jvm 옵션 수정 등을 사용할 수 있다.

<br>

## Exception (예외)
예외는 개발자가 구현한 로직에서 발생하며 개발자가 다른 방식으로 처리가능한 것들로 JVM은 정상 동작한다.

예외가 주로 발생하는 원인
- 사용자의 잘못된 데이터 입력
- 잘못된 연산
- 개발자가 로직을 잘못 작성
- 하드웨어, 네트워크 오작동
- 시스템 과부하

<br>

### Exception의 2가지 종류
1. Checked Exception : 예외처리가 필수이며, 처리하지 않으면 컴파일되지 않는다. JVM 외부와 통신(네트워크, 파일시스템 등)할 때 주로 쓰입니다.
    - RuntimeException 이외에 있는 모든 예외
    - IOException, SQLException 등
2. Unchecked Exception : 컴파일 때 체크되지 않고, Runtime에 발생하는 Exception을 말한다.
    - RuntimeException 하위의 모든 예외
    - NullPointerException, IndexOutOfBoundException 등

<br>

### Exception Handling
예외를 방지하기 위한 기술적인 처리를 의미한다. 

JAVA에서 모든 예외가 발생하면 (XXX)Exception 객체를 생성한다. 

예외를 처리하는 방법에는 크게 2가지가 있다.

1. 직접 try ~ catch 를 이용해서 예외에 대한 최종적인 책임을 지고 처리하는 방식
2. throws Exception 을 이용해서 발생한 예외의 책임을 호출하는 쪽이 책임지도록 하는 방식 (주로 호출하는 쪽에 예외를 보고할 때 사용)

<br>

#### 예외 잡기 (try ~ catch 구문)
로직 중에 예외가 발생할지도 모르는 부분에 try ~ catch 구문으로 보험 처리

- try 에는 위험한 로직이 들어가고, catch 에는 예외 발생 시 수행할 로직이 들어간다.
- 예외가 발생한 다음의 코드들은 실행되지 않으며 catch 구문으로 넘어갑니다.
- catch 구문은 else if 처럼 여러개 쓸 수 있습니다. (하위 Exception부터 작성)
- finally 는 마지막에 실행하고 싶은 로직이 들어가며, 대표적으로 .close() 가 있습니다. <br>
    - Java7부터 Try-with-Resource로도 처리 가능
        - 장점 1: Try-Finally는 시스템 문제가 발생하면 **스택 추적**이 어렵다는 문제점 발생 (앞의 예외를 덮는다) 
        - 장점 2: 코드 가독성 향상 

<br>

#### 예외 던지기 (throws 구문)
예외 처리를 현재 메소드가 직접 처리하지 않고 호출한 곳에다가 예외의 발생 여부를 통보한다. 

호출한 메소드는 이걸 또 던질건지 직접 처리할 건지 정해야 한다. (return보다 강력)



<br>

[출처]

- <https://github.com/GimunLee/tech-refrigerator/blob/master/Language/JAVA/Error%20%26%20Exception.md#error--exception/>