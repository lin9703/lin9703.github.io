---
layout: post
title: "MVC, MVP, MVVM"
author: "Lin"
tags: Android
---
안드로이드 앱을 개발할 때 사용할 수 있는 여러 아키텍처 패턴들이 있다.
- MVC, MVP, MVVM 등

<br>
이들은 M(Model)과 V(View)를 공통적으로 가지고 있다.
- Model: 데이터 또는 데이터를 생성하거나 업데이트
- View: UI 또는 화면을 표시
<br>
프로그램에서 Presentation Logic과 Business Logic를 구현하는데 데이터와 UI는 필수적이다.

> Presentation Logic: 실제 눈에 보이는 GUI(Graphic User Interface)로서 화면을 구성하는 코드 <br>
> Business Logic: 데이터를 보여주기 위해서 DB를 검색하거나 GUI 화면에서 새롭게 발생한 데이터를 DB에 저장하는 등 실제적인 작업을 하는 코드 <br>
> [출처](https://blog.naver.com/blayan/220569833085)

<br>
Logic들이 커지고 복잡해지면서 의존성은 더 강해지고, 앱은 유지보수하기 더 어려워진다. <br><br>
<ins>-> 이를 해결하기 위해 다양한 아키텍처 패턴들이 존재하며, <br>결국 M-V 사이의 관계를 어떻게 처리하느냐에 따라 패턴을 구분 지을 수 있다.</ins>
<br><br><br>

---

# MVC (Model View Controller)
### 프로그램을 각각의 역할에 따라 Model, View, Controller로 나누어 설계한 아키텍처 패턴

### 1) 구조
<img src="https://blog.kakaocdn.net/dn/7IE8f/btqBRvw9sFF/AGLRdsOLuvNZ9okmGOlkx1/img.png"  width="400">

- Controller : 사용자의 입력(Action)을 받고 처리하는 부분
<br><br>

### 2) 동작 순서 
1. 사용자의 모든 Action은 Controller에 들어오게 됩니다.
2. Controller는 Action에 해당하는 Model을 업데이트합니다.
3. Controller는 업데이트 결과에 따라 View를 선택합니다. <br>
(Controller와 View는 1:n 관계로, 여러 개의 View를 관리할 수 있다.)
4. View는 Model을 이용하여 화면을 나타냅니다. <br>
(Controller는 View를 선택만 할 뿐, 직접 업데이트 하지 않는다. View는 Controller를 알지 못 한다.)
5. MVC에서 View가 업데이트 되는 방법
- View가 Model을 이용하여 직접 업데이트 하는 방법
- Model에서 View에게 Notify 하여 업데이트 하는 방법
- View가 Polling으로 주기적으로 Model의 변경을 감지하여 업데이트 하는 방법

--> View를 업데이트하기 위해서는 결국 Model-View 사이에 의존성이 존재하게 된다. <br>
특히, 안드로이드에서는 Activity(or Fragment)가 Controller와 View를 모두 처리하기 때문에, 한 클래스 내에서 M-V-C 모두 처리하는 문제점이 발생한다.
<br><br>

### 3) 장점 
단순하고 보편적으로 사용되는 패턴
<br><br>

### 4) 단점
Model과 View 사이의 의존성 발생 --> 앱이 커지고 복잡해질수록 유지보수 어려움
<br><br><br>

---

# MVP (Model View Presenter)
### MVC에서 파생된 Model과 View 간의 의존성이 없는 아키텍처 패턴

### 1) 구조
<img src="https://blog.kakaocdn.net/dn/clZlsT/btqBTLzeUCL/IDA8Ga6Yarndgr88g9Nkhk/img.png"  width="400">

- Presenter : View에서 요청한 정보로 Model을 가공하여 View에 전달해주는 부분 (View와 Model을 붙여주는 접착제 역할)
<br><br>

### 2) 동작 순서 
1. 사용자의 모든 Action은 View를 통해 들어오게 됩니다.
2. View는 데이터를 Presenter에 요청합니다.
3. Presenter는 Model에게 데이터를 요청합니다.
4. Model은 Presenter에서 요청받은 데이터를 응답합니다.
5. Presenter는 View에게 데이터를 응답합니다.
6. View는 Presenter가 응답한 데이터를 이용하여 화면을 나타냅니다. <br>
(View와 Presenter는 1:1 관계입니다. Presenter는 해당 View를 참조하고 있습니다.)<br>
(Presenter는 View의 Model 인스턴스를 가지고, Model과 View 사이의 매개체 역할을 합니다.)

--> Presenter가 Model-View 사이에서 관리를 해주기 때문에 Model-View 의존성이 없다. <br>
하지만, 앱이 커질수록 View-Presenter의 의존성이 강해지는 문제점이 발생한다.<br><br>

### 3) 장점 
Model-View 의존성이 없다.
<br><br>

### 4) 단점
View-Presenter가 1:1 관계이기 때문에 서로 간의 의존성 커진다. <br>
필요한 클래스 개수가 많아진다.
<br><br><br>

---

# MVVM (Model View ViewModel)
### MVC에서 파생된 Model-View와 Controller-View 간의 의존성도 고려하여 각 구성 요소가 독립적으로 작성되고 테스트되도록 설계된 아키텍처 패턴

### 1) 구조
<img src="https://blog.kakaocdn.net/dn/CiXz0/btqBQ1iMiVT/staXr7UO95opKgXEU01EY0/img.png"  width="400">

- ViewModel : View를 표현하기 위해 만든 Model로서 View를 나타내주기 위한 Model이자 View를 나타내기 위한 데이터 처리를 하는 부분 
<br><br>

### 2) 동작 순서 
1. 사용자의 모든 Action은 View를 통해 들어오게 됩니다.
2. ViewModel은 Action에 해당하는 Presentation Logic을 처리하여 View에 데이터를 전달합니다. <br>
(ViewModel은 View를 참조하지 않아 독립적이다. ViewModel-View는 1:n 관계)
3. View는 자신이 이용할 ViewModel을 선택해 바인딩하여 업데이트를 받게 됩니다. <br>
(Command 패턴이나 Data Binding을 이용하여 View-ViewModel 간 의존성을 없앨 수 있다.)
4. Model이 변경되면 해당하는 ViewModel을 이용하년 View가 자동으로 업데이트 됩니다. <br>
(ViewModel은 View를 나타내주기 위한 Model이자, View의 Presentation Logic을 처리)

--> MVP와 마찬가지로 Model-View 의존성이 없다. <br>
또한, MVP처럼 View-ViewModel이 1:1 관계가 아니라 독립적이기 때문에 이 사이에서 의존성도 없다.

<br>

> Command 패턴: 요청을 객체 형태로 캡슐화하여 사용자가 보낸 요청을 나중에 이용할 수 있도록 메서드 이름, 매개변수 등 요청에 필요한 정보를 저장 또는 로깅, 취소할 수 있게 하는 패턴 <br>
> Data Binding: 공급자와 소비자의 데이터 원본을 함게 바인딩하고 동기화하는 기술 (안드로이드에서는 JAVA에서 처리하던 일을 Xml에서 처리한다.) [출처](https://brunch.co.kr/@oemilk/107)

<br>

### 3) 장점 
Model-View 의존성이 없다.<br>
View-ViewModel 의존성이 없다. (Command 패턴과 Data Binding 사용)<br>
중복되는 코드 모듈화 가능.
<br><br>

### 4) 단점
ViewModel 설계가 쉽지 않다.
<br><br><br>

---

<br>[참고 블로그1](https://brunch.co.kr/@oemilk/113)
<br>[참고 블로그2](https://beomy.tistory.com/43)
