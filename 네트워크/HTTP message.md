# HTTP 메세지

## 1. HTTP 메세지 구조

<img style="width:250px" src="https://velog.velcdn.com/images/fdsa200/post/020976af-b65e-4cb2-9463-0241e582b8e7/image.png">

메세지는 시작라인, 헤더, 공백라인, 본문의 구조로 구성된다.

- **시작라인** : 어떤 메시지인지
- **헤더** (HTTP headers) : 속성
- 공백라인 (CRLF)
- **본문** (body) : 데이터

<br>

## 2. HTTP 메세지 문법

- **요청 메시지(request)**: 웹 서버에 어떤 동작을 요구한다.

  ```
  <메서드> <요청 URL> <HTTP 버전>
  <헤더>
  
  <엔티티 본문>
  ```

- **응답 메시지(response)**: 요청의 결과를 클라이언트에게 돌려준다.

  ```
  <HTTP 버전> <상태 코드> <이유 문구>
  <헤더>
  
  <엔티티 본문>
  ```

<br>

### 2.1) 시작라인 (start-line)

- **요청 메시지 (request)**

  - <span style="color:red">HTTP 메서드</span> : 클라이언트 측에서 서버가 리소스에 대해 수행해주길 바라는 동작 (GET, POST 등)


  - <span style="color:#ff2288">요청 URL</span> : 요청 대상이 되는 리소스를 지칭하는 완전한 URL 또는 URL의 경로 구성요소


  - <span style="color:#00FF11">HTTP 버전</span> : 메시지에서 사용 중인 HTTP 버전 (`HTTP/<메이저>.<마이너>`)

- **응답 메시지 (response)**

  - <span style="color:#ff7f00">HTTP 버전</span>

  - <span style="color:#ff2288">상태 코드</span> (status code) : 요청 중에 무엇이 일어났는지 설명하는 세 자리 숫자 (200, 404 등)
    - 2xx : 성공

    - 4xx : 클라이언트 에러
    - 5xx : 서버 에러


  - <span style="color:#00FF11">이유 문구</span> (reason-phrase) : 사람이 이해할 수 있는 짧은 상태 코드 설명 글

<br>

### 2.2) 헤더 (Header)

```bash
harder-field = field-name “:” OWS field-value OWS (OWS:띄어쓰기 허용, 띄어도 되고 안 띄어도 되고)
```

- **헤더들(Headers)**: `이름: 값` 쌍의 목록,으로 구성된 0개 이상의 헤더들
  - **http 전송에 필요한 모든 부가 정보**
  - ex) 메세지 바디의 내용, 메세지 바디의 크기, 압축, 인증, 요청 클라이언트 정보 등등 모든 필요한 metadata가 있다.
- 사용자 정의 헤더 추가 가능

<br>

### 2.3) 본문 (Body)

- 실제 전송할 데이터
- HTML 문서, 이미지, 영상, JSON 등등 byte로 표현할 수 있는 모든 데이터 전송 가능하다.

<br>

## 3. HTTP 메서드 종류

| 메서드  | 설명                                                    | 메시지 본문 여부 |
| ------- | ------------------------------------------------------- | ---------------- |
| GET     | 서버에서 어떤 문서를 가져온다.                          | no               |
| HEAD    | 서버에서 어떤 문서에 대해 헤더만 가져온다.              | no               |
| POST    | 서버가 처리해야 할 데이터를 보낸다.                     | yes              |
| PUT     | 서버에 요청 메시지의 본문을 저장한다.                   | yes              |
| TRACE   | 메시지가 프락시를 거쳐 서버에 도달하는 과정을 추적한다. | no               |
| OPTIONS | 서버가 어떤 메서드를 수행할 수 있는지 확인한다.         | no               |
| DELETE  | 서버에서 문서를 제거한다.                               | no               |

<br>

- **PUT**

  : 서버가 요청의 본문을 가지고 요청 URL의 이름대로 새 문서를 만들거나, 이미 URL이 존재한다면 본문을 사용해서 교체한다. (전체 수정)

- **POST**

  : 서버에 입력 데이터를 전송하기 위해 설계되었다. (부분 수정)

<br>

## 참고 자료

- https://www.inflearn.com/course/http-웹-네트워크

- https://developer.mozilla.org/ko/docs/Web/HTTP/Status
- [HTTP 완벽 가이드](http://m.yes24.com/Goods/Detail/15381085)
