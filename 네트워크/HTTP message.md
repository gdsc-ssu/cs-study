## HTTP 메세지

### http 메세지 구조

<img style="width:250px" src="https://velog.velcdn.com/images/fdsa200/post/020976af-b65e-4cb2-9463-0241e582b8e7/image.png">

메세지는 시작라인, 헤더, 공백라인, 본문의 구조로 구성된다.

---

### 시작라인 (start-line)

**요청메세지**

```bash
request-line = <span style="color:#ff7f00">method</span> SP(공백) <span style="color:#ff2288">request-target</span> SP <span style="color:#00FF11">HTTP-version</span> CRLF(엔터)
```

- <span style="color:red">HTTP 메서드</span>
  - GET : 리소스 조회 (데이터 달라고 요청)
  - POST : 요청 내역 처리 (데이터 받아오기)
  - PUT : 리소스 생성 혹은 대체 (url이 존재하면 데이터 교체, 존재하지 않으면 생성)
  - DELETE : 삭제 요청 (지워주세요)
- <span style="color:#ff2288">요청 대상</span> (/search?q=hello%hl=ko)
  - absolute-path[?query] (절대경로[?쿼리])
  - 절대경로 = “/”로 시작하는 경로
- <span style="color:#00FF11">HTTP 버전</span>

<br>

**응답메세지**

```bash
status-line = <span style="color:#ff7f00">method</span> HTTP-version</span> SP <span style="color:#ff2288">status-code</span> SP <span style="color:#00FF11">reason-phrase</span> CRLF
```

- <span style="color:#ff7f00">HTTP 버전</span>
- <span style="color:#ff2288">HTTP 상태 코드</span> : 요청 성공, 실패를 나타냄
  - 2xx : 성공
  - 4xx : 클라이언트 요청 오류
  - 5xx : 서버 내부 오류
- <span style="color:#00FF11">이유 문구</span> : 사람이 이해할 수 있는 짧은 상태 코드 설명 글

---

### 헤더 (Header)

```bash
harder-field = field-name “:” OWS field-value OWS (OWS:띄어쓰기 허용, 띄어도 되고 안 띄어도 되고)
```

- **http 전송에 필요한 모든 부가 정보**<br />
  ex) 메세지 바디의 내용, 메세지 바디의 크기, 압축, 인증, 요청 클라이언트 정보 등등 모든 필요한 metadata가 있음.
- 사용자 정의 헤더 추가 가능

---

### messege body (본문)

- 실제 전송할 데이터
- HTML 문서, 이미지, 영상, JSON 등등 byte로 표현할 수 있는 모든 데이터 전송 가능

### 출처

https://www.inflearn.com/course/http-웹-네트워크

https://developer.mozilla.org/ko/docs/Web/HTTP/Status
