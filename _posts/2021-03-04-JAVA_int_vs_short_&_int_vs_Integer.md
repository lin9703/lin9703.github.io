---
layout: post
title: "JAVA int vs short / int vs Integer"
author: "Lin"
tags: JAVA 
---
### CS Study Day 20 - Part1

<br>

## int vs short
- char, short : 이와 같은 정수 자료형 타입으로 표현하면 메모리 공간을 효율적으로 사용할수는 있으나 연산의 효율성은 떨어진다.
    - size : 2byte(16bits)
- int : int형보다 작은 크기의 데이터를 가지고 연산을 진행할 경우, 그 데이터를 일단 int형으로 바꿔서 연산을 진행한다. 
따라서 산술 연산시, 자료형을 int형으로 선언해야 중간에 불필요한 변환 과정을 거치지 않게 되어 연산 효율이 좋다.
    - size : 4byte(32bits)

<br>

## int vs Integer
- int
    - Primitive 자료형
    - 산술 연산이 가능하며, null 값을 가질 수 없다.
- Integer
    - Wrapper 클래스(객체)
    - Unboxing을 하지 않으면 산술 연산이 불가능하지만, null 값을 가질 수 있다.
    - Collection, null 값이 필요한 경우 사용한다.

- size
    - Object : 8 byte
    - Integer : 16 byte
    - Integer를 참조하는데 4 byte
    - 따라서 Integer의 size = 20 byte
    - int의 size : 4 byte
    - 5배 차이가 난다.
