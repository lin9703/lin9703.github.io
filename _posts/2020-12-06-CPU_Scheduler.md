---
layout: post
title: "CPU 스케줄러"
author: "Lin"
tags: 운영체제
---
### CS Study Day 2 - Part4

<br>

# CPU 스케줄러 (CPU Scheduler)
CPU가 하나의 프로세스 작업이 끝나면 다음 프로세스 작업을 수행해야 한다. <br>
상황에 맞게 CPU를 어떤 프로세스에 배정하여 효율적으로 처리하는지가 중요하다. <br>
스케줄링 대상은 *Ready Queue*에 있는 프로세스들이다.
- 조건: 오버헤드 ↓ / 사용률 ↑ / 기아 현상 ↓
- 목표
    1. Batch System: 가능하면 많은 일을 수행. 시간보단 처리량이 중요
    2. Interactive System: 빠른 응답 시간 / 적은 대기 시간 
    3. Real-time System: 기한(deadline)에 맞추기
    
CPU 스케줄링에는 2가지가 존재한다.
- 비선점형(Non-Preemptive) 스케줄링: 프로세스 종료 or I/O 등의 이벤트가 있을 때까지 실행 보장 (처리시간 예측 어려움)
- 선점형(Preemptive) 스케줄링: OS가 CPU의 사용권을 선점할 수 있는 경우 (강제 회수 가능)

<br>

### FCFS(First Come First Served)
#### 특징
- 큐에 도착한 순서대로 CPU 할당 
- 비선점형 스케줄링

#### 문제점
- Convoy Effect 발생: 소요시간이 긴 프로세스가 먼저 도달하면 효율성이 떨어짐 <br>
(실행 시간이 짧은 게 뒤로 가면 평균 대기 시간이 길어짐)

<br>

### SJF(Shortest Job First)
#### 특징
- 다른 프로세스가 먼저 도착했어도 CPU burst time이 짧은 프로세스 먼저 할당
- 비선점형 스케줄링
- FCFS보다 평균 대기 시간 감소, 짧은 작업에 유리

#### 문제점
- starvation: 효율성을 추구하는 게 중요하지만 특정 프로세스가 지나치게 차별 받을 수 있다. <br>
긴 프로세스는 영원히 CPU를 할당받을 수 없는 경우가 생길 수도 있다.

<br>

### SRT(Shortest Remaining time First)
#### 특징
- 선점형 스케줄링: 현재 수행 중인 프로세스의 남은 burst time보다 더 짧은 CPU burst time을 가지는 프로세스가 도착하면 CPU를 뺏긴다.
- 새로운 프로세스가 도착할 때마다 새로운 스케줄링이 이뤄진다.

#### 문제점
- starvation: 효율성을 추구하는 게 중요하지만 특정 프로세스가 지나치게 차별 받을 수 있다. <br>
- 새로운 프로세스가 도달할 때마다 스케줄링을 다시하기 때문에 CPU burst time(CPU 사용시간)을 측정하기 어렵다 

<br>

### Priority Scheduling
#### 특징
- 우선순위가 가장 높은 프로세스에게 CPU를 할당 (정수가 작을수록 우선순위가 높음)
- 비선점형 스케줄링: 더 높은 우선순위의 프로세스가 도착하면 Ready Queue의 Head에 넣는다.
- 선점형 스케줄링: 더 높은 우선순위의 프로세스가 도착하면 실행중인 프로세스를 멈추고 CPU 선점 

#### 문제점
- starvation: 효율성을 추구하는 게 중요하지만 특정 프로세스가 지나치게 차별 받을 수 있다. 
- 무기한 봉쇄(Indefinite blocking): 실행 준비는 되어있으나 CPU를 사용하지 못 하는 프로세스를 CPU가 무기한 대기하는 상태 

#### 해결책
- aging: 오래 기다리면 우선순위를 높여준다. 