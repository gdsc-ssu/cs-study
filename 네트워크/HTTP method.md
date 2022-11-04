# HTTP 메서드의 종류와 속성

## HTTP 메서드의 종류

> [GET](#get) [POST](#post) [PUT](#put) [DELETE](#delete) [PATCH](#patch) HEAD OPTIONS CONNECT TRACE

### GET

- 특정 리소스를 조회하는 메서드
  ( GET [URI] : URI에 있는 리소스(정보)를 주세요 )
- 서버에 전달하고 싶은 데이터는 query를 통해서 전달.
- 특정 범위를 지정해서 요청을 할수도 있다.
  (header 부분에 " Range: [바이트크기] "를 추가하면 가능, 단 서버가 범위요청을 지원해야 한다.)

### POST

- 세가지 역할로 나눌 수 있음.

1. 새 리소스 생성
2. 요청 데이터 처리
   (단, 그 데이터를 처리하는 방법이 미리 정의되어 있어야 함.)
3. 다른 메서드로 처리하기 애매한 경우 POST로 사용.
   **(POST는 단순 데이터 등록 뿐만 아니라 정해놓은 모든 데이터를 활용하는 일을 처리할 수 있음.)**

### PUT

- 리소스를 대체 - 리소스가 존재하면 대체 (덮어쓰기) - 리소스가 없으면 생성
  **- 클라이언트가 리소스를 식별**(리소스를 위치를 지정)

PUT의 주의할 점은 덮어쓰기가 될때 <span style="background-color:#ffdce1;color:black;">완전히</span> 대체된다는 것이다.

<span style='background-color:#dddddd;' > ex) /user/name = {"aaa":20,"bbb":30} 일때
put /user/name = {"aaa": 30 }이라는 메소드를 요청하면
"aaa"만 바뀌는게 아닌 /user/name의 리소스 전체가 바뀌는 것이므로 "bbb"는 사라진다
결과 : /user/name = {"aaa":30}</span>

> put과 post의 차이
> POST는 데이터를 생성할 때 uri를 미지정하여 어디에 서버가 알아서 생성하지만, PUT은 클라이언트에서 URI경로를 지정하여 그곳에 생성시킨다.

### PATCH

- 리소스의 부분 변경
  (가끔 PATCH를 지원안하는 환경에서 부분 변경을 하고 싶으면 <span style='background-color:#999bbb'>POST</span>를 사용하면 된다.)
- PUT과는 다르게 부분만 변경이 된다.

<span style='background-color:#dddddd;' > ex) /user/name = {"aaa":20,"bbb":30} 일때
PATCH /user/name = {"aaa": 30 }이라는 메소드를 요청하면
"aaa"만 바뀐다.
결과 : /user/name = {"aaa":30,"bbb":30}</span>

### DELETE

- 리소스를 제거한다.
  (해당하는 URI에 있는 리소스를 제거한다.)

### 그 외

- HEAD : GET메서드의 요청과 동일한 응답을 요구하지만, 응답 body를 포함하지 않음.
- OPTIONS : 대상 리소스에 대한 통신 가능 옵션(메서드)을 설명
- CONNECT : 대상 리소스로 식별되는 서버에 대한 터널을 설정 (거의 사용안함)
- TRACE : 대상 리소스에 대한 경로를 따라 메세지 루프백 테스트를 수행 (거의 사용안함)

---

## HTTP 메서드의 속성

### 안전(safe)

- 호출해도 리소스를 변경하지 않는다.
  - 만약 리소스를 계속 호출해서, 로그 같은게 쌓여서 장애가 발생한다면?
    → 안전은 해당 호출할때의 리소스의 상황만 반영, 그런부분까지 고려하지 않는다.

### 멱등(idempotent)

- 한번 호출하든 100번 호출하든 결과가 똑같다.
- 멱등 메서드
  - <span style="color:skyblue;">GET</span> : 한 번 조회하든, 두 번 조회하든 같은 결과가 조회됨.
  - <span style="color:skyblue;">PUT</span> : 결과를 대체한다. 같은 요청을 몇 번 하든 최종 결과는 똑같다.
  - <span style="color:skyblue;">DELETE</span> : 결과를 삭제한다. 같은 요청을 여러번 해도 결국 삭제된 결과는 똑같다.
  - <span style="color:red;">POST</span> : 멱등이 아니다! 여러번 호출하면 같은 결제가 중복해서서 발생할 수 있다.
- 멱등은 외부 요인으로 중간에 리소스가 변경되는 것 까지는 고려하지 않는다.
  사용자 1 : GET → username:A, age:20
  사용자 2 : PUT → username:A, age:30
  사용자 1 : GET → username:A, age:30
  → 이런식으로 사용자 2의 영향으로 조회된 값이 바뀌었다고 하더라도 외부 요인으로 값이 바뀐 것이기 때문에 여전히 멱등하다고 판단한다.

- 멱등의 활용
  자동 복구 메커니즘
  → 서버가 정상응답을 못주었을 때 클라이언트가 같은 요청을 다시 해도 되는가?에 대한 판단 근거로 사용. (멱등이면 여러번 재요청 가능, 멱등이 아니면 불가능)

### 캐시가능 (cacheable)

> 캐싱(caching) : 주어진 리소스의 복사본을 저장하고 있다가 요청 시에 그것을 제공하는 기술.

- 응답 결과 리소스를 캐시해서 사용가능한가?
- <span style="color:skyblue;">GET</span>, <span style="color:skyblue;">HEAD</span>,<span style="color:skyblue;">POST</span>,<span style="color:skyblue;">PATCH</span> 캐시 가능
  - 실제로는 GET, HEAD 정도만 캐시로 사용
- 기본 캐시 키(primary cache key)는 요청 메서드 그리고 대상 URI로 구성.(본문 내용이 있으면 그것도 포함)

->POST, PATCH는 가능은 하지만 구현이 어려워서 잘 사용하지 않음.
(GET, HEAD와는 다르게 POST, PATCH는 본문 내용(body)까지 캐시 키(key)로 고려해야 하는데, 구현이 쉽지 않음.)

![](https://velog.velcdn.com/images/fdsa200/post/7e7434ff-a7c8-4113-a059-2dadda5290ac/image.png)

사진 출처 : https://kyun2da.dev/CS/http-%EB%A9%94%EC%86%8C%EB%93%9C%EC%99%80-%EC%83%81%ED%83%9C%EC%BD%94%EB%93%9C/
