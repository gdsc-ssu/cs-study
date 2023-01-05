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