---
layout: post
title: "gRPC 서비스와 HTTP API 비교"
author: "Lin"
tags: 네트워크 
---
### CS Study Day 21 - Part1

<br>

## gRPC
- 최신 버전의 IDL(Interface Definition Lanaguage)로 proto3를 사용합니다. 
- Java, C ++, Python, Java Lite, Ruby, JavaScript, Objective-C 및 C #에서 사용 가능합니다. 
- SSL / TLS를 사용하여 서버를 인증하고 클라이언트와 서버간에 교환되는 모든 데이터를 암호화합니다. 
- HTTP 2.0을 사용하여 기존 HTTP1.1에 비해 통신 성능이 뛰어나고, 확장 가능한 API를 지원합니다. 
- gRPC에선 클라이언트 응용 프로그램을 서버에서 함수를 바로 호출 할 수 있어 분산 MSA(Micro Service Architecture)를 쉽게 구현 할 수 있습니다.

<br>

[출처]
- <https://chacha95.github.io/2020-07-05-gRPC4//>
- <https://docs.microsoft.com/ko-kr/aspnet/core/grpc/comparison?view=aspnetcore-5.0/>
- <https://blog.banksalad.com/tech/production-ready-grpc-in-golang/?gclid=Cj0KCQiAs5eCBhCBARIsAEhk4r49fuzNq2LYhEVUuZu6bm1nxyEqhZYHYo4iOulZ3SjOkDjpZ6zWkSMaAhwJEALw_wcB/>

