---
layout: post
title: "스케쥴러 (장기, 중기, 단기)"
author: "Lin"
tags: 운영체제 CSStudy
---
### CS Study Day 1 - Part4

<br>

# 스케줄러 (Scheduler)
프로세스는 종료될 때까지 수많은 Queue를 돌아다닌다. OS는 이 큐 안에 있는 프로세스 중 하나를 선택해야 하며, 이를 스케줄러가 담당한다.

프로세스를 스케줄링 하기 위한 Queue에는 3가지 종류가 존재한다. 
- Job Queue: 현재 시스템 내에 있는 모든 프로세스의 집합
- Ready Queue: 현재 메모리 내에 있으면서 CPU를 잡아 실행되기를 기다리는 프로세스의 집합 
- Device Queue: 각각의 Device마다 I/O 작업을 대기하고 있는 프로세스의 집합

각각의 Queue에 프로세스를 넣고 빼주는 스케줄러에도 3가지 종류가 존재한다. 

<br>

## 장기 스케줄러(Long-term scheduler or job scheduler)
메모리는 한정되어 있는데 많은 프로세스들이 메모리에 한꺼번에 올라올 경우, 
대용량 메모리(일반적으로 디스크)에 임시로 저장된다. 
이 pool(디스크)에 저장되어 있는 프로세스 중 어떤 프로세스에 메모리를 할당하여 Ready Queue로 보낼지 결정한다. 
- 메모리와 디스크 사이의 스케줄링 담당
- 프로세스에 메모리(및 각종 리소스)를 할당
- 실행 중인 프로세스의 수 제어
- 프로세스의 상태: New -> Ready(in memory)

<br>

## 단기 스케줄러(Short-term scheduler or CPU scheduler)
- CPU와 메모리 사이의 스케줄링 담당
- Ready Queue에 존재하는 프로세스 중 어떤 프로세스를 running 시킬지 결정
- 프로세스에 CPU를 할당
- 프로세스의 상태: Ready -> Running -> Waiting -> Ready

<br>

## 중기 스케줄러(Medium-term scheduler or Swapper)
현 시스템의 메모리에 너무 많은 프로그램에 동시에 올라가는 것을 조절한다. 
- 여유 공간 마련을 위해 프로세스를 메모리에서 디스크로 쫓아냄 (Swapping 기법)
- 프로세스에서 memory를 deallocate
- 실행 중인 프로세스의 수 제어
- 프로세스의 상태: Ready -> Suspended

> Process State - Suspended(Stopped): 외부적인 이유로 프로세스의 수행이 정지된 상태로 메모리에서 내려간 상태이다.
프로세스 전부 디스크로 swap out 된다. 
blocked 상태는 다른 I/O 작업을 기다리는 상태이기 때문에 스스로 ready state로 돌아갈 수 있지만 
Suspended는 외부적인 이유로 배제되었기 때문에 스스로 돌아갈 수 없다. 

<br>

#### Swapping 기법 
- CPU를 쓰기 위해 경쟁하고 있는 우선순위가 낮은 프로세스들을 제거한다. 그리고 추후에 다시 메모리로 불러와서 중단되었던 지점부터 다시 실행을 재게한다. 

<br>

## 스케줄러 과정
![스케줄러 과정](https://user-images.githubusercontent.com/33534771/87003398-82df2880-c1f6-11ea-99da-9deafad24475.png)
- 작업(Job)이 도착하면 Input Queue에서 장기 스케줄러에 의해 메모리에 적재
- 단기 스케줄러에 의해 선택되어 CPU 할당
- Memory Scheduler는 중기 스케줄러의 역할을 하며, 프로세스들이 메모리에서 디스크로 Swap in/Swap out








