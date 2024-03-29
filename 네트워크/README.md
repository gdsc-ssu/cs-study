# 네트워크

<details>
<summary><strong>💡 TCP와 UDP의 차이점</strong></summary>
  <ul>
    <li>TCP는 연결형 서비스, 전송 순서 보장 O, 신뢰성 보장 O, 느림</li>
    <li>UDP는 비연결형 서비스, 전송 순서 보장 X, 신뢰성 보장 X, 빠름</li>
  </ul>
</details>

<details>
<summary><strong>💡 3-handshaking, 4-handshaking이 무엇인지</strong></summary>
  <ul>
    <li>패킷 전송을 위해 논리적 경로를 배정하기 위한 연결 설정 및 해제 과정</li>
  </ul>
</details>

<details>
<summary><strong>💡 3-handshaking, 4-handshaking가 무슨 차이인지</strong></summary>
  <ul>
    <li>연결 해제 과정에서 Server측에서 아직 보낼 데이터가 남아있을 수 있기 때문에 FIN에 대한 ACK만 보내고, Server측에서 데이터를 다 보낸 후 FIN을 보내는 과정이 필요하다.</li>
  </ul>
</details>

<details>
<summary><strong>💡 HTTP와 HTTPS는 무엇인지</strong></summary>
  <ul>
    <li>HTTP</li>
    <ul>
      <li>
      	HyperText Transfer Protocol
      </li>
			<li>
      	웹 상에서 클라이언트와 서버 간에 요청 및 응답으로 정보를 주고 받을 수 있도록 해주는 프로토콜
      </li>
      <li>
      	TCP/UDP를 사용하며, 80번 포트를 사용한다.
      </li>
      <li>
      	비연결성(connectionless) : 클라이언트가 서버에 요청을 보내고 서버가 이에 적절한 응답을 클라이언트로 보낸 후 연결이 바로 끊긴다.
      </li>
      <li>
      	무상태(stateless) : 연결이 끊기는 순간 클라이언트와 서버의 통신은 종료되며 상태 정보를 유지하지 않는다.
      </li>
    </ul>
    <li>HTTPS</li>
    <ul>
      <li>
      	HyperText Transfer Protocol over Secure Socket Layer
      </li>
      <li>
      	HTTP의 보안이 강화된 버전의 프로토콜
      </li>
      <li>
      	기본 TCP/IP 포트로 443번 포트를 사용한다.
      </li>
      <li>
      	소켓 통신에서 일반 텍스트를 이용하는 대신, 웹 상에서 정보를 암호화하는 SSL이나 TLS 프로토콜을 이용해 세션 데이터를 암호화한다.
      </li>
      <li>
      	데이터의 적절한 보호를 보장한다.
      </li>
    </ul>
  </ul>
</details>

<details>
<summary><strong>💡 OSI 7계층과 예시</strong></summary>
  <ul>
    <li>1계층 physical (물리)계층 : 물리적인 연결을 통한 데이터 전송</li>
      	ex) 허브
    <li>2계층 datalink layer(데이터링크 계층) : mac 주소를 사용한 통신, 오류와 재전송 담당.</li>
    		ex) 스위치
    <li>3계층 network layer(네트워크 계층) : 패킷형태의 데이터를 목적지까지 전달</li>
    		ex) ip, route
    <li>4계층 transport layer(전송 계층) : end to end의 신뢰성 있는 통신을 보장</li>
    		ex) tcp, udp
    <li>5계층 session layer(세션 게층) : 응용프로그램간의 대화를 위한 구조 제공 및 관리</li>
    		ex) ssh, tls
    <li>6계층 presentation layer(프리젠테이션 계층) : 데이터 포맷 결정, 포맷을 상호 변환</li>
    		ex) ASCII, JPEG 등
    <li>7계층 application layer(응용 계층) : 사용자 인터페이스 역할</li>
    		ex) http, DNS 등
  </ul>
</details>