---
layout: post
title: "Array vs LinkedList"
author: "Lin"
tags: 자료구조
---
### CS Study Day 1 - Part1

<br>

### Array
1. 논리적 저장 순서와 물리적 저장 순서 일치
2. 메모리 공간 연속적 차지

### LinkedList
1. 논리적 저장치 순서와 물리적 저장 순서 불일치 
2. 메모리 공간 불연속적 차지
3. 사용자는 제일 첫 번째 노드의 위치만 알고 각 노드들은 자기 다음 원소만 아는 상태 (Tree에서 사용할 때 유용)

<br>

### 1. 데이터 접근 속도
#### Array
- index로 접근하면 O(1) 
- Random Access 가능

#### LinkedList
- 순차적으로 검색하기 때문에 O(N)

<br>

### 2. 데이터 삽입/삭제 속도
#### Array
- 데이터를 중간이나 맨 앞에 삽입/삭제 할 경우, Shift 과정이 필요해 O(N)

#### LinkedList
- 맨 앞, 맨 뒤에 삽입/삭제는 O(1)
- 중간에 삽입/삭제 할 경우에 위치를 찾고(O(N)), 삽입/삭제 연산을 진행하기 때문에 O(N)

<br>

### 3. 메모리 할당
#### Array
- Array가 선언되자 마자 Compile time에 할당
- 정적 메모리 할당 

#### LinkedList
- 새로운 노드가 추가 될 때 runtime에 할당
- 동적 메모리 할당








