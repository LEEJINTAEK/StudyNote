# TCP/IP

<br />

## TCP & IP

<br />

TCP / IP를 사용하면 한 컴퓨터가 데이터 패킷을 컴파일하고 올바른 위치로 전송하여 인터넷을 통해 다른 컴퓨터와 통신 할 수 있다.

<br />
<br />

TCP(Transmission Control Protocol)는?

- 신뢰성 있고, 무결성을 보장하는 연결을 통해 데이터를 안전하게 전송해주는 전송 프로토콜
- 한 기기에서 다른 기기로 데이터 전송하는 것을 담당
- Transport Layer

<br />

자세하게!!

- TCP는 많은 양의 데이터를 가져 와서 패킷으로 컴파일 한 다음 동료 TCP 계층에서 수신하도록 전송하여 패킷을 유용한 정보 / 데이터로 바꾸는 역할을 한다.
- TCP는 전달받은 패킷을 재조립하고, 패킷에 손상이 있거나 손실된 패킷이 있다면 재전송을 요청하는 패킷을 전송하여 재전송 받는다.(신뢰성)

<br />
<br />

IP(Internet Protocol)는?

- 패킷들이 가장 효율적인 방법으로 최종 목적지로 갈 수 있도록 해주는 프로토콜
- 프로토콜은 데이터의 조각을 최대한 빨리 대상 IP 주소로 보내는 역할을 표시
- Internet Layer

<br />

자세하게!!

- IP는 올바른 목적지를 찾는 패킷 GPS 역할.
- 지도의 관점에서 IP를 생각하면 IP 계층은 고속도로에서 운전하는 자동차와 마찬가지로 각 패킷은 게이트웨이 컴퓨터 (도로 표지판)를 통과하여 패킷을 올바른 목적지로 전달하는 역할을 한다.

<br />
<br />

## Layer?

<br />

TCP/IP가 많이 사용되면서 흔히 사용되던 OSI 7계층을 더욱 추상화 한 TCP/IP 4계층이 등장 <br />

<img width="410" alt="layer" src="https://user-images.githubusercontent.com/109197023/225010388-fba3663d-7e3e-44d0-ad3e-54d82ea737a7.PNG">

<br />

간단하게 요약해보면

1. 네트워크 액세스 계층(Network Access Layer)

- OSI 7계층의 물리계층과 데이터 링크 계층에 해당
- TCP/IP 패킷을 네트워크 매체로 전달하는 것과 네트워크 매체에서 TCP/IP 패킷을 받아들이는 과정을 담당
- 에러 검출 기능(Detecting errors), 패킷의 프레임화(Fraimg packets)
- 네트워크 접근 방법, 프레임 포맷, 매체에 대해 독립적으로 동작하도록 설계.
- 물리적인 주소로 MAC을 사용
- LAN, 패킷망, 등에 사용됨

2. 계층 인터넷 계층(Internet Layer)

- OSI 7계층의 네트워크 계층에 해당
- 어드레싱(addressing), 패키징(packaging), 라우팅(routing) 기능을 제공
- 네트워크상 최종 목적지까지 정확하게 연결되도록 연결성을 제공하게 됨.
- 프로토콜 종류 – IP, ARP, RARP

3. 계층 전송 계층(Transport Layer)

- OSI 7계층의 전송 계층에 해당
- 애플리케이션 계층의 세션과 데이터그램(datagram) 통신서비스 제공
- 통신 노드 간의 연결을 제어하고, 신뢰성 있는 데이터 전송을 담당한다.
- 프로토콜 종류 – TCP, UDP

4. 계층 응용 계층(Application Layer)

- OSI 7계층의 세션 계층, 표현 계층, 응용 계층에 해당한다.
- 프로그램(브라우저)가 직접 인터액트하는 레이어. 데이터를 처음으로 받는곳
- 다른 계층의 서비스에 접근할 수 있게 하는 애플리케이션을 제공
- 애플리케이션들이 데이터를 교환하기 위해 사용하는 프로토콜을 정의
- HTTP, SMTP등의 프로토콜을 가진다.
- TCP/UDP 기반의 응용 프로그램을 구현할 때 사용한다.
- 프로토콜 종류 – FTP, HTTP, SSH

<br />
전공과목 내용이므로 이정도만 숙지하자

<br />
<br />

## 참고자료

> https://www.youtube.com/watch?v=BWOJc7K9Jw8

> https://nordvpn.com/ko/blog/tcp-ip-protocol/

> https://coding-factory.tistory.com/613
