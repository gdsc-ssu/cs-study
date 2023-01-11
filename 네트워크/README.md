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

<details>
<summary><strong>💡 웹사이트에 접속했을 때 어떤 일이 일어나는가?</strong></summary>
    <li> ex) www.naver.com 을 주소창에 입력하면 어떤 일이 벌어질까?</li><br>    
    <ol>
    <li>사용자가 웹 브라우저를 통해 찾고 싶은 웹 페이지의 URL 주소를 입력함.</li>
    <li>사용자가 입력한 URL 주소 중에서 도메인 네임(domain name) 부분을 DNS 서버에서 검색함.</li>
    <li>DNS 서버에서 해당 도메인 네임에 해당하는 IP 주소를 찾아 사용자가 입력한 URL 정보와 함께 전달함.</li>
    <li>웹 페이지 URL 정보와 전달받은 IP 주소는 HTTP 프로토콜을 사용하여 HTTP 요청 메시지를 생성함. 이렇게 생성된 HTTP 요청 메시지는 TCP 프로토콜을 사용하여 인터넷을 거쳐 해당 IP 주소의 컴퓨터로 전송됨.</li>
    <li>이렇게 도착한 HTTP 요청 메시지는 HTTP 프로토콜을 사용하여 웹 페이지 URL 정보로 변환됨.</li>
    <li>웹 서버는 도착한 웹 페이지 URL 정보에 해당하는 데이터를 검색함.</li>
    <li>검색된 웹 페이지 데이터는 또다시 HTTP 프로토콜을 사용하여 HTTP 응답 메시지를 생성함. 이렇게 생성된 HTTP 응답 메시지는 TCP 프로토콜을 사용하여 인터넷을 거쳐 원래 컴퓨터로 전송됨.  </li>
    <li>도착한 HTTP 응답 메시지는 HTTP 프로토콜을 사용하여 웹 페이지 데이터로 변환됨. </li>
    <li>변환된 웹 페이지 데이터는 웹 브라우저에 의해 출력되어 사용자가 볼 수 있게 됨.</li>
    </ol>
</details>


<details>
<summary><strong>💡 HTTP 메소드</strong></summary>
  <ul>
    <li>POST: 데이터 생성 (Create)</li>
    <li>GET: 데이터 조회 (Read)</li>
    <li>PUT: 데이터 전체 수정 (Update/Replace)</li>
    <li>PATCH: 데이터 부분 수정 (Update/Modify)</li>
    <li>DELETE: 데이터 삭제 (Delete)</li>
  </ul>
</details>

<details>
<summary><strong>💡 Public IP와 Private IP의 차이</strong></summary>
  <ul>
  	<li>공인 IP (Public IP)</li>
		<ul>
    		<li>전세계에서 유일한 IP로, ISP(인터넷 서비스 공급자)가 제공하는 IP주소이다.</li>
    		<li>외부에 공개되어 있기 때문에 인터넷에 연결된 다른 장비로부터 접근이 가능하다.</li>
    		<li>방화벽 등 보안 설정을 해줄 필요가 있다.</li>
		</ul>
	<li>사설 IP (Private IP)
		<ul>
    		<li>특정 네트워크 안에서 사용되는 IP주소</li>
    		<li>IPv4 의 부족으로 인해 모든 네트워크가 공인 IP를 사용하는 것은 불가능하기 때문에 네트워크 안에서 라우터를 통해 할당받는 가상의 주소이다.</li>
    		<li>별도의 설정 없이는 외부에서 접근 불가능하다.</li>
		</ul>
  </ul>
</details>