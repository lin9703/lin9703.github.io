---
layout: post
title: "<안드로이드 프로그래밍> Ch.4 UI 상태 유지하기 (AAC ViewModel)"
author: "Lin"
tags: Android
---

> 본 게시물은 [실무에 바로 적용하는 안드로이드 프로그래밍](https://book.naver.com/bookdb/book_detail.nhn?bid=18123166) 책을 기반으로 작성되었습니다.

<br>

[실습 코드](https://github.com/lin9703/android-practice-code/tree/main/GeoQuiz)

# AAC ViewModel
안드로이드는 적절한 시점에 리소스를 제공하지만, 화면 회전과 같은 환경 변화에 따른 액티비티 소멸 및 재생성은 문제가 생길 수 있다.

-> AAC ViewModel에 UI 데이터를 저장해 앱의 UI 상태가 유실되는 결함 해결 

<br>
**AAC ViewModel** : 모델 데이터를 화면에 보여주는 기능 수행 

- 생명주기 인식하는 컴포넌트를 포함하고 생명주기 관련 API를 제공하는 androidx.lifecycle 패키지의 일부 
- 화면에서 필요한 모든 `데이터를 한곳에서 종합`하고 `데이터 형식화` 가능 
    - `데이터 형식화`: 프레젠테이션 로직 코드를 액티비티와 분리하여 액티비티 간결화 가능 <br>
        -> 액티비티는 화면에 나타나는 것을 처리하는 것만 집중하고 보여줄 데이터를 결정하는 내부 로직은 신경 쓰지 않아도 된다.

<br>

## ViewModel 생명주기 
장치의 구성 변경이 생겨도 계속 존재하다가 액티비티가 종료될 때만 소멸

ViewModel 인스턴스는 `액티비티의 생명주기와 연동`
- 액티비티 상태 변화와 무관하게 액티비티가 종료될 때까지 메모리에 남아있다가 액티비티가 종료되면 소멸 
- onCleared() 함수: ViewModel 인스턴스 소멸 전 호출 

<br>

## 액티비티와 ViewModel의 관계 

액티비티와 ViewModel은 `단방향 관계`이다.

액티비티는 ViewModel을 참조하지만, ViewModel은 액티비티를 참조하지 않는다.

ViewModel이 액티비티나 다른 뷰의 참조를 가지면 `메모리 유실`이 생길 수 있다. <br>
참조되는 개체를 가비지 컬렉터가 메모리에서 제거할 수 없어진다. (강한 참조) <br>
#### 문제점 
1. 액티비티 인스턴스가 메모리에서 제거되지 않아 이 인스턴스가 사용하는 `메모리 유실`
2. ViewModel 인스턴스가 현재 사용되지 않는 과거의 액티비티의 참조를 갖게 되어 ViewModel 인스턴스가 과거 액티비티의 뷰를 변경하려고 하면 `IllegalStateException` 발생 

<br>

