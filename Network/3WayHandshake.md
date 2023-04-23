# 3-Way Handshake와 4-Way Handshake

3-Way Handshake는 TCP의 접속, 4-Way Handshake는 TCP의 접속 해제 과정이다.

- 포트(PORT) 상태 정보
  - CLOSED: 포트가 닫힌 상태
  - LISTEN: 포트가 열린 상태로 연결 요청 대기중
  - SYN_RCV: SYNC 요청을 받고 상대방의 응답을 기다리는중
  - ESTABLISHED: 포트 연결 상태

- 플래그 정보
  - TCP Header에는 CONTROL BIT(플래그 비트, 6bit)가 존재하며, 각각의 bit는 "URG-ACK-PSH-RST-SYN-FIN"의 의미를 가진다.  
    즉, 해당 위치의 bit가 1이면 해당 패킷이 어떠한 내용을 담고 있는 패킷인지를 나타낸다.
  - SYN(Synchronize Sequence Number) / 000010  
    연결 설정. Sequence Number를 랜덤으로 설정하여 세션을 연결하는 데 사용하며, 초기에 Sequence Number를 전송한다.
  - ACK(Acknowledgement) / 010000  
    응답 확인. 패킷을 받았다는 것을 의미한다.  
    Acknowledgement Number 필드가 유효한지를 나타낸다.  
    양단 프로세스가 쉬지 않고 데이터를 전송한다고 가정하면 최초 연결 설정 과정에서 전송되는 첫 번째 세그먼트를 제외한 모든 세그먼트의 ACK 비트는 1로 지정된다고 생각할 수 있다.
  - FIN(Finish) / 000001  
    연결 해제. 세션 연결을 종료시킬 때 사용되며, 더 이상 전송할 데이터가 없음을 의미한다.

<br>

### TCP의 3-Way Handshake

- TCP 통신을 이용하여 데이터를 전송하기 위해 네트워크 연결을 설정(Connection Establish)하는 과정
- 양쪽 모두 데이터를 전송할 준비가 되었다는 것을 보장하고, 실제로 데이터 전달이 시작하기 전에 한쪽이 다른 쪽의 준비 완료를 알 수 있도록 한다.
- 즉, TCP/IP 프로토콜을 이용해서 통신을 하는 응용 프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전ㅇ에 세션을 수립하는 과정이다.

<br>

**3-Way Handshake의 매커니즘**  
TCP 통신은 PAR(Positive Acknowledgement with Re-transmission)을 통해 신뢰적인 통신을 제공한다.  

![](https://velog.velcdn.com/images/jimeaning/post/4bacf47d-505d-466f-8e74-f6ef1a94dbc7/image.png)


**PAR을 사용하는 기기는 ack를 받을 때까지 데이터 유닛을 재전송한다.**

수신자가 데이터 유닛(세그먼트)이 손상된 것을 확인하면(Error Detection에 사용되는 transport layer의 checksum을 활용), 해당 세그먼틀르 없앤다. 그러면 sender는 positive ack가 오지 않은 데이터 유닛을 다시 보내야 한다.  
=> 이 과정에서 클라이언트와 서버 사이에 3개의 segment가 교환된다.(SYN, SYN/ACK, ACK) 이것이 3-Way Handshake의 매커니즘이다.

<br>

**작동 방식**
- Client는 Server와 연결하기 위해 3-Way Handshake를 통해 연결 요청을 하게 된다.
- 일반적으로 생각하는 Client와 Server는 모두 서로 연결 요청을 먼저 할 수 있어, 연결 요청을 먼저 시도한 요청자가 Client, 연결 요청을 받은 수신자가 Server 쪽이라고 보면 된다.
- SYN(Synchronization): 연결요청, 세션을 설정하는데 사용되고 초기에 시퀀스 번호를 보낸다.
- ACK(Acknowledgement): 보낸 시퀀스 번호에 TCP 계층에서의 길이 또는 양을 더한 것과 같은 값을 ACK에 포함하여 전송한다.
  - 동기화 요청에 대한 답변: Client의 Sequence Number +1을 하여 ACK로 돌려준다.

<br>

### TCP의 4-Way Handshake
4-Way Handshake는 연결을 해제(Connection Termination)하는 과정이다. 여기서 FIN 플래그를 이용한다.
- FIN(finish): 세션을 종료시키는데 사용되며, 더이상 보낸 데이터가 없음을 나타낸다.

<br>

**Termination의 종류**  
TCP는 대부분의 connection-oriented 프로토콜과 같은 두 가지 연결 해제 방식이 있다.

1. Graceful connection release(정상적인 연결 해제)  
   정상적인 연결 해제에서는 양쪽이 모두 커넥션을 닫을 때까지 연결되어 있다.
2. Abrupt connection release(갑작스런 연결 해제)
   1. 갑자기 한 TCP 엔티티가 연결을 강제로 닫는 경우
   2. 한 사용자가 두 데이터 전송 방향을 모두 닫는 경우

<br>


**작동 방식 (Graceful)**   
연결 종료 요청 역시 일반적으로 생각하는 Client와 Server 둘 다 연결 요청을 먼저 할 수 있다. 따라서 연결 요청을 먼저 시도한 요청자를 Client, 연결 요청을 받은 수신자를 Server로 생각하면 된다.  

>**Half-Close 기법**  
처음 보내는 종료 요청인 FIN 패킷에 실질적으로 ACK가 포함되어 있을 수 있는데, 이는 Half-Close 기법을 사용하기 때문이다.  
>- 즉, 연결을 종료하려고 할때 완전히 종료하지 않고 반만 종료한다.
>- Half-Close 기법을 사용하면 종료 요청자가 처음 보내는 FIN 패킷에 승인 번호를 함께 담아서 보내게 된다. 이때 승인 번호의 의미는 "일단 연결은 종료할 건데 귀는 열어 둘게, 이 승인 번호까지 처리했으니까 보낼 거 있으면 더 보내"가 된다.
>- 이후 수신자가 남은 데이터를 모두 보내고 나면 다시 요청자에게 FIN 패킷을 보냄으로써 모든 데이터가 처리되었다는 신호 FIN을 보낸다. 그럼 요청자는 그때 나머지 반을 닫으면서 좀 더 안전하게 연결을 종료할 수 있게 된다.

<br>

**작동 방식 (Abrupt)**  
RST(TCP reset) 세그먼트가 전송되면 갑작스러운 연결 해제가 수행되는데, RST 세그먼트는 다음과 같은 경우에 전송된다.

1. 존재하지 않는 TCP 연결에 대해 비SYN 세그먼트가 수신된 경우
2. 열린 커넥션에서 일부 TCP 구현이 잘못된 헤더가 있는 세그먼트가 수신된 경우
   - RST 세그먼트를 보내 해당 커넥션을 닫고 공격을 방지한다.
3. 일부 구현에서 기존 TCP 연결을 종료해야 하는 경우
   - 연결을 지원하는 리소스가 부족할 때
   - 원격 호스트에 연결할 수 없고 응답이 중지되었을 때
  

<br>

#### 참고
[TCP/UDP와 3-Way Handshake & 4](https://velog.io/@averycode/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-TCPUDP%EC%99%80-3-Way-Handshake4-Way-Handshake)