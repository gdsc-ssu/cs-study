
# DNS & DHCP

## 📌 DNS

### 도메인과 DNS

- 도메인이란 IP주소를 사람이 기억하기 쉽게 이름을 부여한 것이다.
- 도메인을 변환하기 위해 브라우저가 인터넷 자원을 로드할 수 있도록 도메인 이름을 IP주소로 변환시켜 주는 것이 DNS이다.

### DNS 과정

1. DNS Query
    - DNS 서버에서 Domain name을 이용해 IP주소를 받아온다. 이때 Domain Name Server에 접속하는 유저에 대해서 Round Robin 방식으로 IP를 할당한다.
2. IP Communication
    - IP를 받아온 유저는 리퀘스트 메시지 발송을 통하여 정상적인 네트워크 통신을 실시한다.
- DNS 서버는 웹서버 주소에 해당하는 IP주소 테이블을 가지고 있는 서버라고 보면된다.

### DNS 서버 종류

![Untitled](https://user-images.githubusercontent.com/85864699/210156709-7cc806e4-292d-4022-841b-e034402a64d5.png)

사진 출처: [https://gentlysallim.com/dns란-뭐고-네임서버란-뭔지-개념정리/](https://gentlysallim.com/dns%EB%9E%80-%EB%AD%90%EA%B3%A0-%EB%84%A4%EC%9E%84%EC%84%9C%EB%B2%84%EB%9E%80-%EB%AD%94%EC%A7%80-%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC/)

- Root DNS Server
    - ICANN(국제 인터넷주소 관리기구)이 직접관리하는 서버로, TLD(최상위 도메인) DNS 서버 IP들을 저장해두고 안내하는 역할을 한다.
- TLD(최상위 도메인) DNS Server
    - 도메인 등록기관이 관리하는 서버로 Authoritative DNS 서버 주소를 저장해두고 안내하는 역할을 한다.
- Authoritative DNS Server
    - 실제 개인 도메인과 IP주소의 관계가 기록/저장/변경되는 서버이다.
    - 일반적으로 도메인/호스팅 업체의 네임서버를 말하지만 개인 DNS 서버를 구축한 경우에도 여기에 해당된다.
- Recursive DNS Server
    - 인터넷 사용자가 가장 먼저 접근하는 DNS 서버이다.
    - 위 3개의 DNS 서버를 매번 거친다면 효율이 안좋아질 수 밖에 없으니 한번 거친 후 얻은 데이터를 일정 기간(TTL)동안 캐시라는 형태로 저장해두는 서버이다.
    - 대표적으로 ISP DNS 서버와 Cloud flare와 같은 Public DNS서버가 있다.

### DNS의 라운드 로빈 방식

![Untitled](https://user-images.githubusercontent.com/85864699/210156712-404ad84e-90c1-4a4d-aaa8-596d98fe3fc1.png)

이미지 출처:[https://velog.io/@eu_nzi/네트워크-DNS-round-robin의-방식](https://velog.io/@eu_nzi/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-DNS-round-robin%EC%9D%98-%EB%B0%A9%EC%8B%9D)

- Roun Robin이란 DNS 서버 구성방식 중 하나로, Domain에 대한 IP요청 쿼리시, Round Robin 방식으로 IP주소를 반환한다.
- DNS 서버에 대해 Round Robin 형식으로 구성할 경우 자동으로 시간에 따라 스케쥴링이 변화하기 때문에 로드 밸런서가 필요가 없다.
- 단점
    - 서버의 수만큼 공인 IP주소가 필요하다
        - 부하분산을 위해 서버의 수를 늘리기 위해서는 그만큼의 공인 IP가 필요하다.
    - 균등하게 분산되지 않는다.
        - 모바일 사이트에 접속을 하게 되면 스마트폰의 경우 캐리어 게이트웨이라는 프록시 서버를 경유한다.
        - 프록시 서버에서는 이름 변환 결과가 일정 시간 동안 캐싱되므로 같은 프록시 서버를 경유하는 접속은 항상 같은 서버로 접속된다.
    - 서버가 다운되어도 확인이 불가능하다.
        - 웹서버의 부하나 접속 수 등의 상황에 따라 질의 결과를 제어할 수 없다 → 헬스체크 불가능
        - 간혹 유저들이 다운된 서버로 연결이 되기도 한다.
- 해결책
    - 다중화 구성방식
        - 각 AP서버를 헬스체크 후 이상이 감지되면 VIP를 정상 AP서버로 인계하는 방식을 사용한다.
            
            🎵 **AP서버 란?**
            
            서버 그 자체 네트워크가 연결되어있기만 하다면, 그 네트워크를 통해 서버와 Endpoint 간의 통신을 할 수 있는 Server이다. 
            
            **🎵 다중화란?**
            
            다중화란, 장애가 발생해도 예비 운용장비로 시스템의 기능을 계속할 수 있도록 하는 것을 말한다.
            
        - DNS Server Table에 실시간으로 AP서버의 상태를 확인할 수 있는 칼럼 및 함수를 추가하여 요청될 경우 서버 상태를 확인하여 우회 루트를 제공하거나 에러를 전송하는 방식을 말한다.
    - 가중치 편성 방식
        - 각 웹 서버에 가중치를 가미해서 분산 비율을 변경한다.
        - 가중치가 높은 서버일 수록 빈번하게 선택되므로 처리 능력이 높은 서버에 가중치를 높게 설정해야한다.
    - 최소 연결방식
        
        ![Untitled](https://user-images.githubusercontent.com/85864699/210156714-cf565401-e39c-4e44-a747-a12de5f626e7.png)
        
        이미지 출처: [https://tecoble.techcourse.co.kr/post/2021-11-07-load-balancing/](https://tecoble.techcourse.co.kr/post/2021-11-07-load-balancing/)
        
        - 로드 밸런서를 도입했을 경우, 접속 클라이언트가 가장 적은 서버를 선택한다.
        - 로드 밸런서에서 실시간으로 connection 수를 관리하거나 각 서버에게 주기적으로 알려주는 것이 필요하다.

## 📌 DHCP

### DHCP 프로토콜

- 동적 호스트 설정 프로토콜( Dynamic Host Configuration Protocol)이다.
- IP주소와 서브넷마스크, 기본 게이트웨이 IP주소, DNS서버 IP주소를 자동으로 일정 시간동안 할당해주는 프로토콜이다.
    
    🎵 **네임서버란?**
    
    영문 도메인을 네 자리의 IP 주소로 매핑시켜 주는 서버이다.
    
- IP주소 렌탈이라고 생각하면 되는데 고정 IP에 비해 address pool을 유연하게 사용가능하다.
- 렌탈이기 때문에 임대기간(IP Lease TIme)을 명시하여 그 기간 동안만 단말이 IP주소를 사용하도록 하는 것이다.
- 단말이 임대기간 이후에도 계속 해당 IP주소를 사용하고자 한다면 IP주소 임대기간 갱신을 DHCP서버에 요청해야하고 , 더이상 필요하지 않다면 IP주소 반납절차를 수행하게 된다.

### DHCP의 장점

- PC의 수가 많거나 PC 자체 변동사항이 많은 경우 IP 설정이 자동으로 되기에 효율적으로 사용가능하고, IP주소를 자동으로 할당해주기 때문에 IP충돌을 막을 수 있다.

### DHCP의 단점

- DHCP서버에 의존되기 때문에 서버가 다운되면 IP 할당이 제대로 이루어지지 않는다.

### DHCP의 구성

- DHCP 서버
    - 인터넷을 제공해주는 곳의 서버에서 실행되는 프로그램으로 일정한 범위의 IP주소를 다른 클라이언트에게 할당하여 자동으로 설정하게 해주는 역할을 한다.
- DHCP 클라이언트
    - 클라이언트들은 시스템이 시작하면 DHCP서버에 자신의 시스템을 위한 IP주소를 요청하고, DHCP서버로 부터 IP주소를 부여받으면 TCP/IP 설정은 초기화되고, 다른 호스트와  TCP/IP를 사용해 통신을 할 수 있게 된다.
    - 서버에게 IP를 할당받으면 TCP/IP통신을 할 수 있다.
- DHCP 임대절차
    
    ![Untitled](https://user-images.githubusercontent.com/85864699/210156715-62986a49-d484-4f91-9e4a-4658f1dc5a6e.png)
    
    사진출처:[https://velog.io/@hidaehyunlee/더-편리한-인터넷을-위해-DHCP-DNS-프로토콜](https://velog.io/@hidaehyunlee/%EB%8D%94-%ED%8E%B8%EB%A6%AC%ED%95%9C-%EC%9D%B8%ED%84%B0%EB%84%B7%EC%9D%84-%EC%9C%84%ED%95%B4-DHCP-DNS-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
    
    - IP 임대절차에 사용되는 DHCP 메세지는 4가지이다.
    1. **DHCP Discover**
        - 패킷 방향 : 클라이언트 → DHCP서버
        - 주요 파라미터(패킷내용):  클라이언트 MAC주소
        - 클라이언트가 **DHCP서버를 찾기위한 메세지.**
        - Discover 패킷에 IP주소가 필요한 호스트의 MAC주소가 담겨져 있어서 DHCP서버가 응답할 때 패킷을 수신할 수 있게 된다.
    2. **DHCP Offer**
        - 패킷 방향: DHCP서버 → 클라이언트
        - 주요 파라미터(패킷내용)
            - Client MAC
            - Your IP(단말에 할당할 IP주소)
            - Subnet Mask
            - Router
            - DNS
            - 임대 시간
            - DHCP Server Identifier : DHCP Offer메세지를 보낸 DHCP서버의 IP주소
        - 단순히 DHCP서버의 존재만을 알리지 않고, **클라이언트에 할당할 IP주소 정보를 포함한 다양한 네트워크를 정보를 함께 실어 클라이언트에 전달한다.**
    3. **DHCP Request**
        - 패킷 방향: 클라이언트 → DHCP서버
        - 주요 파라미터(패킷내용)
            - Client MAC : 단말의 MAC주소
            - Requested IP Address
            - DHCP Server Identifier : 만약 두개 이상의 DHCP 서버가 DHCP Offer을 보낸 경우 단말이 둘 중 하나를 고르게 되는데 선택받은 서버의 IP주소가 여기에 들어간다.
            - 즉, DHCP Server Identifier에 명시된 DHCP서버에게 DHCP Request 메세지를 보내어 단말 IP주소를 포함한 네트워크 정보를 얻는다.
        - 단말이 DHCP서버들의 존재와 네트워크 정보를 알았으니 DHCP Request 메세지를 통해 **하나의** DHCP 서버를 선택하고 해당 서버에게 **단말이 사용할 네트워크 정보**를 요청한다.
    4. DHCP Ack
        - 패킷 방향: DHCP서버 → 클라이언트
        - 주요 파라미터(패킷내용) : DHCP Request 패킷의 파라미터와 동일
        - DHCP 절차의 마지막 메세지로, **DHCP 서버가 단말에게 네트워크 정보를 전달해주는 메세지이다.**

## 참고자료

컴퓨터네트워크 강의(한양대학교,이석복,2015)

[https://jwprogramming.tistory.com/35](https://jwprogramming.tistory.com/35)

[https://velog.io/@eu_nzi/네트워크-DNS-round-robin의-방식](https://velog.io/@eu_nzi/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-DNS-round-robin%EC%9D%98-%EB%B0%A9%EC%8B%9D)

[https://gentlysallim.com/dns란-뭐고-네임서버란-뭔지-개념정리/](https://gentlysallim.com/dns%EB%9E%80-%EB%AD%90%EA%B3%A0-%EB%84%A4%EC%9E%84%EC%84%9C%EB%B2%84%EB%9E%80-%EB%AD%94%EC%A7%80-%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC/)

[https://velog.io/@hidaehyunlee/더-편리한-인터넷을-위해-DHCP-DNS-프로토콜](https://velog.io/@hidaehyunlee/%EB%8D%94-%ED%8E%B8%EB%A6%AC%ED%95%9C-%EC%9D%B8%ED%84%B0%EB%84%B7%EC%9D%84-%EC%9C%84%ED%95%B4-DHCP-DNS-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
