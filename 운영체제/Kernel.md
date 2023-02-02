# 👨‍💻 Kernel(커널)

## 🐸 Kernel(커널)이란?

- 운영체제는 컴퓨터의 전원이 켜짐과 동시에 **계속해서** 실행되는 소프트웨어이다.
  - 소프트웨어가 실행되면, 메모리에 올라간다.
  - 크기가 큰 운영체제가 전원이 켜져있는 동안 계속해서 메모리 위에 올라가있다면...?
    - **메모리 낭비가 아주 아주 아주 심해질 것이다.**
- 따라서 운영체제는 필요한 부분만 메모리에 올려놓고, 그렇지 않은 것은 필요할 때만 메모리에 올려서 사용하는 방식을 채택하고 있다.
  - 이때 메모리에 상주하는 부분을 `Kernel(커널)`이라고 한다.
    - 이를 `좁은 의미의 운영체제`라고도 한다.
    - 즉, 운영체제의 핵심이 되는 부분을 뜻한다.

## 🐸 운영체제와 Kernel(커널)

- 넓은 의미의 운영체제는, 커널을 포함하여 시스템 유틸리티 전체를 뜻하는 광범위한 개념이다.
- 즉, 일반적으로 운영체제는 `Kernel`을 말한다.

### 🐾 차이점

- **개념의 차이**
  - 운영체제는 시스템의 자원을 관리하는 시스템 프로그램
  - 커널은 운영체제의 핵심이 되는 프로그램
- **인터페이스의 차이**
  - 운영체제는 사용자와 컴퓨터간 인터페이스
  - 커널은 소프트웨어와 하드웨어간 인터페이스
- **운용 기법의 차이**
  - 운영체제
    - 일괄처리 시스템
    - 다중 프로그래밍 시스템
    - 시분할 시스템
    - 다중처리 시스템
    - 실시간 처리 시스템
    - 다중 모드 처리
    - 분산 처리 시스템
  - 커널
    - 모놀리식 커널
    - 마이크로 커널
- **역할의 차이**
  - 운영체제는 커널의 역할 + 시스템 보안 등의 역할까지
  - 커널은 자원 관리의 역할

## 🐸 Kernel(커널)의 기능

### 🐾 자원 관리로써의 Kernel(커널)

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fv75s4%2Fbtrn0kossMK%2FHikspganIcKi1n0b97x740%2Fimg.png)

- 커널의 자원 관리는 곧 일반적인 **운영체제의 자원관리**를 뜻한다.
- 컴퓨터의 `물리적 자원`과 `추상화 자원`을 관리
  - **추상화**란, 하나뿐인 하드웨어를 여러 사용자가 번갈아가며 사용하게 하는 것이다.
  - 각 사용자들은 하나의 하드웨어를 독점하는 것처럼 느끼게 된다.
  - 물리적 자원을 추상화한 자원의 대표적인 명칭은 아래와 같다.
    - CPU
      - Task / Process
    - Memory
      - Page / Segment
    - Disk
      - File
    - Network
      - Socket

### 🐾 인터페이스로써 Kernel(커널)

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbXqZHy%2Fbtrn0kaXPGC%2F1aF0nbtLfRosvckPRx0D0K%2Fimg.png)

- `Kernel Space`는 `Hardware`와 `User Space` 사이에 위치한다.
  - 어플리케이션이 하드웨어로부터 오는 자원을 관리하고 사용할 수 있게 해준다.
- `User Space`에 `Task` `Process` 등의 추상화 자원이 존재한다.
  - 이들이 `Kernel Space`에 접근할 때는 `System Call Interface`에 접근한다.
  - `System Call Interface`를 통해 사용자는 `Kernel`에서 제공하는 `Protected` 서비스에 접근할 수 있게 된다.
    ![image](https://user-images.githubusercontent.com/44965706/209422757-5ded770c-4915-4b48-96d0-c46f0b8afb0b.png)
- 즉 커널의 주요 기능은 **사용자가 System Call을 통해 컴퓨터 자원을 사용할 수 있게해주는 자원 관리자**라고 할 수 있다.

## 🐸 Kernel(커널)의 유형

![image](https://user-images.githubusercontent.com/44965706/209423133-3e83460b-dcba-479f-9750-40048125434c.png)

### 🐾 모놀리식 Kernel(커널)

- 어플리케이션을 제외한 모든 Kernel System을 커널에서 직접 처리하는 방식이다.
  - VFS (Virtual File System)
  - IPC (InterProcess Communication)
  - File System 등
- 장점
  - 어플리케이션과 Kernel 서비스가 같은 주소 공간에 위치한다
  - 즉, 시스템 콜 및 Kernel 서비스 간 데이터 전달 시 Overhead가 적다.
  - 효율이 좋고, 빠르다.
- 단점
  - 모든 서비스들이 하나의 바이너리로 이루어져 있다.
  - 즉, 일부분만 수정해도 전체에 영향을 미칠 수 있다.
  - 모든 모듈이 유기적으로 연결되어 있어, Kernel 크기가 커질수록 유지보수가 어렵다.
  - 한 모듈의 버그가 시스템 전체에 영향을 끼칠 수 있다.

### 🐾 마이크로 Kernel(커널)

- Kernel Service를 기능에 따라 모듈화하여 각각 독립된 주소 공간에서 실행
  - 이런 모듈을 `서버`라 한다.
    - `서버`들은 독립된 프로세스로 구현된다.
- 마이크로 커널은 서버들간의 통신이다(IPC)
  - **핵심 기능의 커널**은 공유하고, 나머지는 User Process 처럼 사용한다.
    - Process Management
    - Memory Management
    - Network Management
- 장점
  - 각 `Kernel Service`간 의존성이 낮다
  - 모놀리식에 비해 유지보수가 쉽다.
  - Kernel 서비스 서버의 간단한 시작 / 종료가 가능
  - 이론적으로 모놀리식보다 안정적이다.
    - 시스템 전체가 고장날 일은 적기 때문이다.
  - 서버 코드가 Protected Memory에서 실행되므로, 검증된 분야에 적합하다.
    - 의료 컴퓨터 분야 등
- 단점
  - 모놀리식 커널에 비해 낮은 성능을 보인다.
  - 독립된 서버들간 통신 및 Context Switching이 필요하기 때문이다.

## 🔍 참고자료

- 2022-숭실대학교-소프트웨어학부-운영체제-강의자료
- [[OS] 커널(Kernel)이란](https://minkwon4.tistory.com/295)
- [[운영체제] 커널이란?](http://itnovice1.blogspot.com/2019/08/blog-post_83.html)
- [커널과 운영 체제의 차이점](https://ko.gadget-info.com/difference-between-kernel)
