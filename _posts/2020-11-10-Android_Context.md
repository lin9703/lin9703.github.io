---
layout: post
title: "안드로이드의 Context"
author: "Lin"
tags: Android
---


## 안드로이드에서 Context
- Application 환경에 대한 전역 정보를 접근하기 위한 인터페이스
- 추상 클래스이며 실제 구현은 Android 시스템에 의해 제공된다.
- Context를 통해 Resource, Database, SharedPrefernces 등의 시스템 자원을 얻을 수 있다.
- Activity 실행, Intent 브로드캐스팅, Intent 수신 등과 같은 응용 프로그램 수준의 작업을 수행하기 위한 API를 호출할 수 있다.
- Application과 Activity 클래스 둘 다 Context를 확장한 서브 클래스이다.
<br>

안드로이드에서 주로 Application Context와 Activity Context를 사용한다.
<br><br>

## Application Context
안드로이드 애플리케이션 그 자체로, _현재 애플리케이션의 상태_ 를 표현한다.<br>
Application Context는 getApplicationContext() 메서드를 통해 접근 가능하다.<br>
이 Context는 _애플리케이션의 생명주기_ 와 묶여 있다.
생명주기가 현재 Context와 분리된 Context가 필요하거나 Activity 범위보다 큰 Context를 전달할 때 사용한다. 
<br><br>

## Activity Context
_Activity를 표현_ 한다. <br>
Activity Context는 Activity 내에서 사용 가능한 Context이다. <br>
이 Context는 _Activity의 생명주기_ 와 묶여 있어 onDestroy()와 함께 사라진다.
Activity 범위 내에서 Context를 전달하거나 현재 Context에 생명주기가 엮여있는 Context가 필요한 경우에는 Activity Context를 사용한다. 
<br><br>

## 메모리 누수 방지
Context를 잘못 사용하면 메모리 누수를 발생시킬 수 있다. <br>


<br><br>
[참고 블로그 1](https://www.charlezz.com/?p=44580)
<br>[참고 블로그 2](https://shnoble.tistory.com/57)
<br>[참고 블로그 3](https://shinjekim.github.io/android/2019/11/01/Android-context%EB%9E%80/)