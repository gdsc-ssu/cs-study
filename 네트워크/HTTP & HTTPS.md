# HTTP & HTTPS
> 서버와 클라이언트 간 데이터를 주고받는 통신 프로토콜 

## ✅ HTTP (Hyper Text Transfer Protocol)
- 서버/클라이언트 모델을 따라 데이터를 주고 받기 위한 프로토콜
- 인터넷 상에서 하이퍼텍스트를 교환하기 위한 통신 규약
- Using Port : 80 port
    - HTTP 서버 : 80번 포트에서 요청을 기다림
    - 클라이언트 : 80번 포트로 요청 전송
- 애플리케이션 레벨의 프로토콜, **TCP/IP 위에서 작동**
- **stateless 프로토콜** : 상태를 가지지 않는 프로토콜
- Method, Version, Headers, Body 등으로 구성

### ▶️ HTTP 구조
HTTP : 애플리케이션 레벨의 프로토콜, **TCP/IP 위에서 작동** <br>
<div align="center">
<img src="https://user-images.githubusercontent.com/66112716/197479841-51b12482-8f7b-4406-ad70-b7abeb8ad115.png" width="50%">
<img src="https://user-images.githubusercontent.com/66112716/197479899-9f583206-4b83-4ad1-9fc7-50550d45755a.png" width="50%">
</div>

> [사진 출처](https://dev.classmethod.jp/articles/about-http/)

### ▶️ Request 메세지
- `Start line`, `Headers`, `Body`로 이루어짐

1. `Start Line` : 요청의 첫번째 줄
    - HTTP Method : 해당 요청이 의도한 액션의 정의부 (`GET`, `POST`, `DELETE`)
    - Request target : 해당 요청이 전송되는 목표 url
    - HTTP Version : 사용되는 HTTP 버전 정보, ex) `GET/login HTTP/1.1`

2. `Headers` : 요청에 대한 추가 정보(meta data)
    - `Key:value` 형태로 이루어짐
    ```
    Headers: {
        Host: 요청 전송 url ex) www.naver.com
        User-Agent: 요청을 보내는 클라이언트 정보 ex) chrome, firefox, ...
        Content-Type: 해당 요청이 보내는 메세지 body 타입 ex) application/json
        Content-Length: body 내용의 길이
        Authorization: 회원의 인증/인가를 처리하기 위한 로그인 토큰
    }
    ```

3. `Body` : 해당 요청의 실제 내용
    ```
    Body: {
        "user_email" : "gdscssu@google.com"
        "user_password" : "1234"
    }
    ```

### ▶️ Response 메세지
- `Status line`, `Headers`, `Body`로 이루어짐

1. `Status Line` : 응답의 상태줄
    - HTTP Version : 요청의 HTTP 버전
    - Status Code : 응답 메시지의 상태 코드
    - Status Text : 응답 메시지의 상태 설명 텍스트

    ex) `HTTP/1.1 404 NOT FOUND`, `HTTP/1.1 200 SUCCESS` <br>

2. `Headers` : Request message의 Headers와 동일
    - 응답의 추가 정보를 담는 부분
    - Response Message에서만 사용하는 헤더 정보도 있음

3. `Body` : Request message의 Body와 동일
    - 가장 많이 사용되는 Body 데이터 타입 : `JSON`

## ✅ HTTPS (Hyper Text Transfer Protocol Secure)
- HTTP에 **데이터 암호화**가 추가된 프로토콜
- Using Port : 443 port
- 네트워크 상에서 제 3자가 중간에 정보를 볼 수 없도록 데이터 암호화

### ▶️ HTTPS의 암호화 방법
HTTPS : 대칭키 암호화 방식 & 비대칭키 암호화 방식

### ▶️ 대칭키 암호화
- 클라이언트와 서버가 동일한 키를 사용해 암호화/복호화 진행
- 키가 노출될 경우 매우 위험함
- 연산 속도 빠름

### ▶️ 비대칭키 암호화
- 1개의 쌍으로 구성된 공개키와 개인키를 암호화/복호화 하는 데에 사용
- 키가 노출되어도 비교적 안전
- 연산 속도 느림

### ▶️ 비대칭키 암호화
<p align="center"><img src="https://user-images.githubusercontent.com/66112716/157616290-f90cce9c-db9f-494e-8bd6-caa6f1f0b5de.png" width="700" height="250"></p>

> [사진 출처](https://velog.io/@minj9_6/%EB%8C%80%EC%B9%AD%ED%82%A4%EC%99%80-%EB%B9%84%EB%8C%80%EC%B9%AD%ED%82%A4%EB%8A%94-%EB%AC%B4%EC%8A%A8-%EC%B0%A8%EC%9D%B4%EA%B0%80-%EC%9E%88%EC%9D%84%EA%B9%8C)

- **비대칭키 암호화** : 공개키/개인키 암호화 방식
    - **공개키** : 모두에게 공개 가능한 키
    - **개인키** : 본인만 가지고 있는 키 (비공개)

- **공개키 암호화** : 공개키로 암호화를 할 경우 **개인키로만 복호화 가능**
    - 개인키 : 본인만 가지고 있기에 본인만 볼 수 있음
- **개인키 암호화** : 개인키로 암호화할 경우 **공개키로만 복호화 가능**
    - 공개키 : 모두에게 공개
    - 본인이 인증한 정보임을 알아 신뢰성 보장 가능

### ▶️ HTTPS 연결 과정 성립 흐름
1. 클라이언트(브라우저) → 서버로의 최초 연결 시도
2. 서버 : 공개키를 브라우저에 넘김
3. 클라이언트(브라우저) : 인증서(공개키)의 유효성 검사 → 세션키 발급
4. 클라이언트(브라우저) : 세션키 보관, 서버의 공개키로 세션키 암호화해 서버로 전송
5. 서버 : 개인키로 암호화된 세션키 복호화 → 세션키 얻음
6. 클라이언트 & 서버 : 동일한 세션키 공유 → 데이터 전달 시 세션키로 암호화/복호화 진행    
<br>

> 참고 자료 : https://mangkyu.tistory.com/98