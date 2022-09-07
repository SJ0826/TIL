# TCP, UDP

## 프로토콜 계층에서의 메세지 전송과정

![프로토콜 계층](https://user-images.githubusercontent.com/56298540/188804372-2be5ad6e-8d10-4752-91a8-a38f6cd926df.PNG)

1. 프로그램이 Hello, world! 메시지 생성
2. SOCKET 라이브러리에서 OS계층에 메시지 전달
3. OS에서 메시지에 TCP정보를 생성하고 IP 패킷을 생성한다.
4. 네트워크 인터페이스에서 LAN카드를 통해서 나갈 때 Ethernet frame과 함께 나간다.

## TCP란?

![TCP 패킷 정보](https://user-images.githubusercontent.com/56298540/188805048-fc74f506-6ded-471a-83ee-8e22e636185b.PNG)
**전송 제어 프로토콜(Transmission Control Protocl)**을 뜻한다.<br>
말 그대로 전송을 제어하는 프로토콜이다.<br>
IP보다 먼저 생성되어 IP의 단점을 보완한다.

### TCP특징

- 연결지향 - TCP 3 way handshake (가상 연결)<br>
  먼저 연결을 하고 메시지를 보낸다. 서버와 클라이언트가 모두 연결 가능상태여야 동작한다.<br>

  #### TCP 3 way handshake 과정

  ![3 way handshake](https://user-images.githubusercontent.com/56298540/188806499-a60ead32-e2b3-4859-8ccf-8d74e71281c2.PNG)

  1. 클라이언트에서 SYN(접속요청)이라는 메시지를 보낸다.
  2. 서버가 메시지를 받으면 Syn(접속요청)과 ACK(요청 수락)이라는 메시지를 보낸다.
  3. 메시지를 받은 클라이언트가 서버에 ACL(요청수락)을 보낸다. (이 과정에서 데이터도 함께 전송하는 경우도 있다.)
  4. 연결이 되고나면 데이터가 전송된다.<br><br>
     연결 과정에 문제가 생기면 메시지를 보내 않기 때문에 안정성이 보장되고 클라이언트와 서버간의 신뢰가 생성된다.<br>
     하지만 이 과정은 실제로(물리적으로) 연결된 것이 아니다. <br>중간의 노드들은 연결과정에서 제외되고 클라이언트와 최종 서버 간의 논리적 연결일 뿐이다.<br>

- 데이터 전달 보증<br>
  패킷이 중간에 누락이 되면 상대방이 알 수 있다.
- 순서 보장<br>
  만약 서버에 순서가 맞지 않게 도착했다면, 클라이언트에 문제점부터 다시 보내라고 데이터 요청을 한다.
- 신뢰할 수 있는 프로토콜
- 현재는 대부분 TCP 사용

## UDP란?

**사용자 데이터그램 프로토콜(User Datagram Protocol)**을 똣한다.

### UDP 특징

- 하얀 도화지에 비유(기능이 거의 없음)
- 연결지향 - TCP 3 way hankshacke x
- 데이터 전달 보증 x
- 순서 보장 x
- 데이터 전달 및 순서가 보장되지 않지만, 단순하고 빠름
- 정리<br>
  &nbsp;IP와 거의 같다. +PORT + 체크섬 정도만 추가<br>
  &nbsp;애플리케이션에서 추가 작업 필요

### 장점

기능이 없는 만큼 유연성있게 사용자에 맞게 더 최적화가 가능하다.

## 출처

- [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC)
