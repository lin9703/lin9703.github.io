---
layout: post
title: "HTTP와 HTTPS"
author: "Lin"
tags: 네트워크
---
### CS Study Day 2 - Part3

<br>

## HTTP (HyperText Transfer Protocol)
- 인터넷 상에서 클라이언트와 서버가 자원을 주고받을 때 쓰는 통신 규약 
<br><br>

### HTTP의 특징
1. TCP/IP 기반의 통신 방식
2. 비연결 지향
    - 요청에 대한 응답의 데이터를 전송 후 연결 종료
    - 여러 사용자가 요청할 때 각각의 요청 구분 불가능 
3. 단방향성: 사용자의 요청 한 개에 대해 한 개의 응답 방식 

### HTTP의 문제점
1. HTTP는 평문 통신이기 때문에 **도청** 가능
2. 통신 상대를 확인하지 않기 때문에 **위장** 가능
3. 완전성(**정보의 정확성**)을 증명할 수 없기에 **변조** 가능 

*위 세 가지는 다른 암호화하지 않은 프로토콜에도 공통되는 문제점*

### 해결법
1. TCP/IP 구조의 통신은 통신 경로 상에서 패킷을 수집하는 것만으로 도청 가능 <br>
-> 통신 자체에 `SSL(Secure Socket Layer)` or `TLS(Transport Layer Security)`라는 다른 프로토콜을 조합해 암호화 <br>
-> SSL을 조합한 HTTP를 `HTTPS(HTTP Secure)`이라 부른다.

2. HTTP에 의한 통신에는 상대가 누구인지 확인하는 처리가 없기에 누구든지 요청을 보낼 수 있다. <br>
-> `SSL`은 상대를 확인하는 수단으로 **증명서** 제공 (증명서는 신뢰할 수 있는 제 3자 기관에 의해 발행)

3. 서버 또는 클라이언트에서 수신한 내용이 송신측에서 보낸 내용과 일치하다고 보장할 수 없다. <br>
(공격자가 도중에 리퀘스트나 리스폰스를 빼앗아 변조하는 중간자 공격(Man-in-the-Middle)에도 이 사실을 알 수 없다.) <br>
-> 해시 값을 확인하는 방법과 파일의 디지털 서명을 확인하는 방법이 존재하지만 확실하지는 않다.
-> 확실히 방지하기 위해 `HTTPS` 사용
-> SSL에는 인증이나 암호화, 다이제스트 기능 제공  

<br>

## HTTPS (HyperText Transfer Protocol Secure)
- HTTP에 암호화와 인증, 그리고 완정성 보호를 더함 
- HTTP 통신하는 소켓 부분을 `SSL(Secure Socket Layer)` or `TLS(Transport Layer Security)` 프로토콜로 대체 <br>
(HTTP는 원래 TCP와 직접 통신했지만, HTTPS에서 HTTP는 SSL과 통신하고 **SSL이 TCP와 통신**)
- HTTPS의 SSL에서는 공통키 암호화 방식과 공개키 암호화 방식을 혼합한 하이브리드 암호 시스템 사용



