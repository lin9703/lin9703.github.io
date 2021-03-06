---
layout: post
title: "안드로이드 4대 컴포넌트"
author: "Lin"
tags: Android 
---
### CS Study Day 20 - Part3

<br>

Android 앱은 컴포넌트로 구성되어 있다. Activity, Service, Broadcast Receiver, Content Provider이다. 

각 컴포넌트들은 하나의 독립된 형태로 존재하며, 정해진 역할을 수행한다. 컴포넌트들 간의 상호 통신은 Intent라는 일종의 메시지 객체를 사용하여 상호 통신을 진행한다.

<br>

## Activity
- `사용자 인터페이스 화면`을 가지며 특정 작업을 담당하는 컴포넌트
- UI를 갖는 하나의 스크린을 나타낸다.
- 최소 하나 이상의 Activity를 가지고 있어야 한다.
- 매니페스트 파일에 등록되어야 한다.
- 하나 이상의 View를 가질 수 있다.
 
<br>

## Service
- `백그라운드`에서 실행되는 컴포넌트로 오랫동안 실행되는 작업이나 원격 프로세스를 위한 작업을 할 때 사용된다.
- UI가 없다.
- 한 번 시작된 Service는 애플리케이션이 종료되고 다른 앱으로 이동해도 계속 백그라운드에서 실행된다.
- ex) 음악 재생, 네트워크를 통해 데이터를 꺼내오는 작업 등등

<br>

## Broadcast Receiver
- 안드로이드 `단말기`에서 발생하는 다양한 이벤트, 정보를 받고 반응하는 컴포넌트이다.
- 단말기에서 발생하는 일 중 애플리케이션이 알아야 하는 상황이 발생하면 방송해준다.
- 수신기를 통해 상황을 감지하고 적절한 작업을 수행한다.
- UI가 없다.
- ex) 배터리 부족,시스템 부팅, 전화나 문자 수신 등등.

<br>

## Content Provider
- 데이터를 관리하고 다른 애플리케이션 데이터를 제공하는 컴포넌트.
- 데이터는 파일 시스템이나 SQLite 데이터베이스, 웹 상에 저장될 수 있다.
  
<br>

## Intent
- 독립적으로 동작하는 4대 컴포넌트들 간의 상호 통신을 위한 장치이다.
- 4대 컴포넌트의 통신 수단
- 인텐트를 통해 다른 애플리케이션의 컴포넌트를 활성화 시킬 수 있다.


<br>

[출처]

- <https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Android/4%EB%8C%80%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8.md/>