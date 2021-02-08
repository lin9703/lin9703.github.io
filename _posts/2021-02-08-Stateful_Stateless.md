---
layout: post
title: "Stateful vs. Stateless 서비스와 HTTP 및 REST"
author: "Lin"
tags: 네트워크 
---
### CS Study Day 15 - Part3

<br>

대표적인 Stateless 프로토콜로는 UDP와 HTTP 등이 있습니다. 

여기서는 UDP를 예로 들어 보겠습니다. 

아시다시피, UDP는 TCP와 달리 handshaking 과정을 통해 연결 세션을 인증하는 절차를 수행하지 않습니다. 

세션 상태에 관계 없이 단순히 데이터그램을 source에서 destination 쪽으로 전송합니다. 


 
client가 송신하려 했던 모든 데이터가 server쪽에 수신 되었는지 확인하지 않습니다. 

따라서 server쪽은 client와의 세션 정보를 전혀 저장하지 않습니다. 

 


TCP vs. UDP (출처 : https://www.muvi.com/wiki/udpuser-datagram-protocol.html)
 

따라서 UDP는 Client와의 세션 상태에 관계없이 요청에 대한 응답만을 수행합니다.

또한 Client와의 세션 정보를 server가 저장하지 않는다는 점에서 Stateless 하다고 말할 수 있습니다.

 

 

Stateless Service는 이러한 Stateless한 특성,

   1. 세션 정보를 server에 저장하지 않음, 2. 세션 'State(상태)'에 무관한 응답

를 만족하도록 설계된 서비스 구조 입니다. 

 

 

아래와 같은 Stateless 서비스 구조를 생각해 봅시다. 

이번에도 Client A의 요청이 로드밸런서를 통해 Server#1 으로 전달 되었다고 가정해 봅시다.

Stateful 서비스 구조에서는 server에 직접 ClientA와의 세션 정보를 저장했지만.


 
Stateless 서비스 구조에서는 이 정보를  server에 저장하지 않고, 외부 DB에 저장합니다.


 
따라서 ClientA의 요청이 Server#2로 전달 되더라도, Server#2는 DB를 통해 ClientA 정보에 접근 가능합니다.

이러한 Stateless 구조에서는 ClientA의 요청을 Server#1에만 유지되도록 관리할 필요가 없습니다. 

 

 


Stateless Service Architecture
 

 

3. Why Stateless Service?
위에서도 눈치 채셨겠지만, Statelss 구조가 Stateful 구조 대비 갖는 몇가지 장점들로 인해 

최근의 웹서비스 구조는 모두 Stateless 구조 기반을 따르고 있습니다. 

 

 

그렇다면 Stateless Service가 어떤 점에서 유리할까요?

여러가지 이유가 있겠지만, 제가 생각하는  stateless 구조의 가장 큰 이점만 소개하겠습니다.

 

 

바로 Scaling이 자유롭다는 것입니다. 

 

 

트래픽의 급증으로 서버가 scale out된 상황을 생각 해봅시다.

 

- Stateful 서비스의 경우,

client의 세션 정보가 새로 scale out된 서버에 저장 되어 있지 않습니다!

따라서 세션 정보를 옮겨주는 등의 부수적인 관리가 요구 됩니다. 


Scaling Out of Stateful Service
 

-Stateless 서비스의 경우,

어차피 server는 client 세션 관리를 하지 않으므로, 걱정할 필요가 없습니다!


Scaling Out of Stateless Service
 

 

scaling은 최근 웹 서비스들이 요구하는 중요한 기능입니다. 

serverless 구조의 서비스 구현에서는 필수적입니다. 

따라서 최근 웹 서비스 트렌드 동향에 발맞춰, scaling이 자유로운 Stateless 서비스 구조가 각광받고 있습니다. 

 

 

4. Stateless Service 및 HTTP, REST
stateless service를 검색하면 나오는 연관 검색어들이 HTTP, REST 입니다. 

 각 용어 들의 대분류를 해봅시다.

 

Stateless 와 Representational State Transfer (REST)는 '구조(Architecture)' 의 이름 입니다. 

반면 HTTP는 프로토콜 입니다. 

 

그럼 각 용어들의 정의 해봅시다. 

 

2장에서 말했 듯, HTTP는 Stateless한 프로토콜 입니다. 

그리고 REST는 이러한 HTTP 프로토콜 상에 구현된 Resource Oriented Architecture (ROA) 설계 구조 입니다. 

 

따라서 HTTP와 REST 모두 Stateless한 성격을 가진 녀석들이며,

HTTP는 Statelss한 성격을 가진 '프로토콜'

REST는  Stateless한 성격을 가진 '설계 구조' 



 