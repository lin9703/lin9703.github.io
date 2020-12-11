---
layout: post
title: "운영체제"
author: "Lin"
tags: 운영체제
---
### CS Study Day 3 - Part4

<br>

# 운영체제란 
- 하드웨어를 관리하고, 응용 프로그램과 하드웨어 사이에서 인터페이스 역할을 하며 시스템의 동작을 제어하는 시스템 소프트웨어 
- 운영체제는 `시스템의 자원과 동작을 관리하는 소프트웨어`

<br>

### 1. 프로세스 관리
- 운영체제에서 작동하는 응용 프로그램 관리 
- 프로세서(CPU) 관리: 현재 CPU를 점유해야 할 프로세스를 결정하고 할당하며, 이 프로세스 간 공유 자원 접근과 통신 등을 관리 
- 키워드: `프로세스, 스레드`, `스케줄링`, `동기화`, `IPC 통신`

### 2. 저장장치 관리
- 1차 저장장치에 해당하는 Main Memory와 2차 저장장치에 해당하는 하드디스크, NAND, Flash Memory 등을 관리
    - 1차 저장장치
        - 프로세스에 할당하는 메모리 영역의 할당과 해제
        - 각 메모리 영역 간의 침범 방지
        - 메인 메모리의 효율적 활용을 위한 가상 메모리 기능
    - 2차 저장장치
        - 파일 형식의 데이터 저장
        - 파일 데이터 관리를 위한 파일 시스템 관리
- 키워드: `메모리 관리`, `가상 메모리`, `파일 시스템`

### 3. 네트워킹 
- TCP/IP 기반의 인터넷에 연결하거나 응용 프로그램이 네트워크를 사용헐 수 있게 네트워크 프로토콜 지원
- 사용자와 하드웨어 사이에서 응용 프로그램 및 하드웨어를 소프트웨어적으로 제어 및 관리
- 키워드: `TCP/IP`, `기타 프로토콜`

### 4. 사용자 관리
- 한 컴퓨터를 여러 사람이 사용하는 환경을 고려하여 각 계정을 관리할 수 있는 기능 
- 파일이나 시스템 자원에 접근 권한을 지정할 수 있도록 지원 
- 키워드: `계정 관리`, `접근 권한 관리`

### 5. 디바이스 드라이버 
- 여러 하드웨어를 운영체제에서 인식하고 관리하여 응용 프로그램이 하드웨어를 사용 가능하게 지원
- 운영체제 안에 하드웨어를 추상화 해주는 계층인 디바이스 드라이버 존재 
- 디바이스 드라이버 관리 기능 또한 지원
- 키워드: `순차접근 장치`, `임의접근 장치`, `네트워크 장치`
