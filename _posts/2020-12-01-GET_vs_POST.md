---
layout: post
title: "GET, POST 방식의 차이점"
author: "Lin"
tags: 개발지식 CSStudy
---
### CS Study Day 1 - Part3

<br>

둘 다 HTTP 프로토콜을 이용해 서버에 요청할 때 사용하는 방식이다.

<br>

## GET
- 요청하는 데이터가 `HTTP Request Message의 Header 부분의 url`에 담겨서 전송
- url 상에 ? 뒤에 데이터가 붙어 request 요청 <br>
-> 크기가 제한적 <br>
-> 데이터가 그대로 url에 노출 (password와 같은 보안이 필요한 데이터에서는 위험)

<br>

## POST
- 요청하는 데이터가 `HTTP Request Message의 Body` 부분에 담겨서 전송 <br>
-> 데이터 크기가 GET 방식보다 크고 보안적 면에서 낫다. <br>
(하지만 보안적 측면에서 암호화를 하지 않는 이상 비슷하다.)

<br>

## 차이점
#### GET
1. SELECT적인 성향으로 서버에서 데이터를 가져와서 보여주기 위해 사용 (서버의 값이나 상태 등을 변경X)
2. 브라우저에 Caching 가능 (기존에 caching 되었던 데이터가 재응답 가능성 존재) -> Idempotent

#### POST
1. 서버의 값이나 상태를 변경 또는 추가하기 위해 사용 
2. 서버에 동일한 요청을 전송해도 응답은 다 다를 수 있다 -> Non-idempotent









