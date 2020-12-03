---
layout: post
title: "ArrayList vs LinkedList"
author: "Lin"
tags: 자료구조 JAVA CSStudy
---
### CS Study Day 2 - Part1

<br>

ArrayList와 LinkedList는 모두 Java에서 제공한 List 인터페이스를 구현한 Collection 구현체이다. <br>

### ArrayList
내부적으로 데이터를 배열에서 관리하며 데이터의 추가, 삭제를 위해 임시 배열을 생성해 데이터를 복사한다.
![](https://lh5.googleusercontent.com/7pSzmL9zBHuRuDAbWV6NjmYEx2otpkTVCA5aStNUESja4KAhPCllb8Dc277BRSaLEmy4Q-y1GS2X5WwLtylnxWo3q4CkcJRo4DA9PEesAX04HEZmaL9pOIqvlyQ8fWakBg)

### LinkedList
사용자는 제일 첫 번째 노드의 위치만 알고 각 노드들은 자기 다음 원소만 아는 상태 (Tree에서 사요알 때 유용)

<br>

### 1. 데이터 접근 속도
#### ArrayList
- index로 접근하면 O(1) 

#### LinkedList
- 순차적으로 검색하기 때문에 O(N)

<br>

### 2. 데이터 삽입/삭제 속도
#### ArrayList
- 데이터 삽입은 새 array에 기존 항목의 데이터를 복사해야 하기 때문에 최악의 경우 O(N)
- 데이터 삭제는 Shift 과정이 필요하기 때문에 최악의 경우 O(N) <br>
(제거하려는 index가 시작에 가까울수록 더 많은 요소를 이동 / 맨 뒤의 경우 O(1))


#### LinkedList
- 맨 앞, 맨 뒤에 삽입/삭제는 O(1)
- 중간에 삽입/삭제 할 경우에 위치를 찾고(O(N)), 삽입/삭제 연산을 진행하기 때문에 O(N)








