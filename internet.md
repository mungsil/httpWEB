## 인터넷 네트워크
> 컴퓨터는 인터넷을 통하여 통신한다.
>
> 
> 어떻게?

## IP(인터넷 프로토콜)

지정한 IP주소로 데이터를 전달한다.
패킷이라는 통신 단위로 데이터를 주고 받는다.

- 패킷
  
  출발지IP,  목적지IP,  메세지, 기타 등등...을 포함
- 한계
  1. 비연결성
     > 서버가 패킷을 받을 수 없는 상태라면?
  2. 비신뢰성
     > 보낸 패킷이 사라지거나 보낸 순서대로 패킷이 도착하지 않으면?
  3. 프로그램 구분
     > 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상이라면?

- 해결

## TCP
- Transmission Control Protocol
- 세그먼트에는 출발지 PORT, 목적지 PORT, 전송 제어, 순서, 검증 정보... 등이 들어 있다.
- 인터넷 프로토콜 스택의 4계층
  1. 애플리케이션 계층 - HTTP, FTP
  2. 전송 계층 - TCP, UDP
  3. 인터넷 계층 - IP
  4. 네트워크 인터페이스 계층 
- 특징
  1. 연결 지향 (TCP 3 way handshake_ 가상 연결)
  2. 데이터 전달 보증
  3. 순서 보장
  4. 신뢰할 수 있는 프로토콜

- TCP 3 way handshake
 1. 클라이언트 -> 서버
  > SYN 전송
 2. 서버 -> 클라이언트
  > SYN + ACK 응답
 3. 클라이언트 -> 서버
  > ACK 전송

위와 같은 과정으로 connect가 된 후에 데이터 전송이 이루어진다.

 SYN: 접속 요청, ACK: 요청 수락

 ## UDP
 
사용자 데이터그램 프로토콜(User Datagram Protocol)
- ip와 별 다를게 없다. 단, PORT, checksum 개념이 추가되어 있다.
- 데이터 전달 및 순서가 보장되어있지 않지만, 단순하고 빠르다.


## PORT

같은 IP(아파트)내에서 프로세스(동, 호수)를 구분하기 위해 사용된다. 

## DNS
Domain Name System
실제 사용 시에는 DNS 서버를 이용하여 도메인 명을 IP주소로 변환하여 사용한다.
DNS는 아래 문제점을 해결한다.
> IP는 기억하기 어렵다.
> IP는 변경될 수 있다.


 