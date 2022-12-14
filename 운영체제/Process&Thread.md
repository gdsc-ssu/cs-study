# Process and Thread

## 프로그램, 프로세스, 스레드

- 프로그램이란, 저장 상태에 저장되어 있는 파일이 메모리에는 올라가지 않은 정적인 상태를 말한다.
- 프로세스란, 프로그램이 실행되면 해당 파일은 메모리에 올라가게 되고, 이러한 동적인 상태를 말한다.
- 스레드란, 프로세스가 할당받은 자원을 이용하는 실행 단위를 말한다.

## 프로세스와 스레드의 작동 방식

프로그램이 실행되어 메모리에 올라갈때 운영체제는 시스템 자원을 할당해준다. **프로세스**는 메모리 영역을 Code, Data, Stack, Heap 형식으로 할당 받게 되고 이를 각 프로세스마다 독립적으로 사용하게 된다. 때문에 각 프로세스는 서로의 메모리 영역에 접근할 수 없다.

<img width="650" alt="스크린샷 2022-11-04 03 06 32" src="https://user-images.githubusercontent.com/67703882/199800693-d10baefb-1de6-4cbb-9e08-1bdc140accb0.png" style="zoom:70%;" >

- Code 영역 : 프로그램 코드 및 매크로 상수가 기계어 형태로 저장된 영역
- Data 영역 : 전역 변수와 static 변수가 저장되는 영역. 프로그램이 시작할때 할당되어 종료할때 소멸된다.
- Stack 영역 : 함수 내에서 선언된 여러 변수 및 값들이 저장되고 함수 호출시 기록하고 종료되면 제거한다.
- Heap 영역 : 관리가 가능한 데이터 이외의 다른 형태의 데이터를 관리하기 위한 공간. 프로그램이 사용할 메모리 크기를 고려하여 동적으로 메모리 할당이 이뤄진다.

반면 프로세스 내에서 생성된 **스레드**는 Stack 형식으로 할당된 메모리 영역만 따로 할당 받고, 나머지 Code, Data, Heap 영역으로 할당된 메모리 영역은 공유한다. 이러한 스레드를 경량화된 프로세스라고도 한다. 이렇게 생성된 스레드들은 운영체제의 일부인 Schedular 에 의해 독립적으로 관리된다.

<img width="642" alt="스크린샷 2022-11-04 03 07 05" src="https://user-images.githubusercontent.com/67703882/199800788-9b44e66f-6c49-4515-998f-1bc8962ef568.png" style="zoom:50%;" >

## 프로세스와 스레드의 차이

위 내용을 토대로 정리한 프로세스와 스레드의 차이점은 다음과 같다.

- 프로세스
  - 독립적인 메모리 영역을 가지고 있어, 프로세스끼리 접근 불가능
  - 한 프로세스가 강제 종료되도 다른 프로세스가 영향 받지 않음.
  - 프로세스 간의 전환 (=Context Switching) 비용이 상대적으로 크다.
- 스레드
  - 프로세스 내에서 Stack 영역을 제외한 메모리 영역을 공유
  - 한 스레드에서 강제 종료가 되면, 프로세스 내 다른 스레드들이 영향 받음.
  - 스레드 간의 전환 비용이 상대적으로 적다.

> **TMI** : Internet Explorer는 멀티 스레드 방식으로 동작하기 때문에 자원 활용의 효율성은 좋으나 화면에 띄워놓은 여러 페이지 중 한 페이지에서 문제가 생기면 전체가 종료된다. 반면 Chrome은 멀티 태스킹(멀티 프로세스) 방식으로 동작하기 때문에 한 화면에 문제가 생겨도 다른 크롬 화면에 미치는 영향이 적다. 다만 여러 프로세스를 사용하는 것이 낭비일 수는 있다.

#### 여러 스레드를 사용하게 되면?

하나의 프로세스가 여러 작업을 여러 스레드를 이용하여 동시에 처리하는 것을 **멀티스레드** 라고 한다.

멀티 스레드를 사용하게 되면, 어느 부분을 담당하는 스레드가 작업 시간이 조금 걸리거나 block 이 되더라도 다른 스레드들이 실행되고 있기 때문에 사용자 입장에서 그 프로그램이 Interactive 하게 보일 수 있도록 한다. 또 스레드는 하나의 프로세스 메모리 영역에서 실행하기 때문에, 새로운 프로세스를 생성하는 것보다 스레드를 생성하는 것이 비용이 더 적게 들어간다.

그럼 스레드를 프로세스 내에서 무작정 많이 만드는 것이 좋을까?

<img width="319" alt="스크린샷 2022-11-04 02 32 00" src="https://user-images.githubusercontent.com/67703882/199793327-e655c5a9-d093-4967-8e67-55e49a5dc93e.png"  >

그렇지는 않다. 위 그래프를 보면 스레드 수가 증가할수록 CPU 처리량이 증가하다가, 어느 임계점을 넘어가면 다시 감소하는 것을 볼 수 있다. 이는 Thread Switching 비용 역시 함께 증가하기 때문이다.

## IPC : 프로세스 간 통신

**IPC (Inter-Process Communication)** 이란, 프로세스 혹은 스레드 간에 데이터 및 정보를 주고 받기 위한 메커니즘 중 하나이다. 커널은 IPC 라는 내부 프로세스간 통신을 제공하고, 프로세스는 커널이 제공하는 IPC 설비를 이용해 프로세스 간 통신을 할 수 있게 된다.

> **커널(Kernel)** 이란? : 운영체제 자체도 소프트웨어기 때문에 메모리에 올라가야 사용할 수 있다. 이때 메모리 공간을 절약하기 위해 운영체제 중 항상 필요한 부분, 즉 핵심적인 부분만을 메모리에 올려놓고 그렇지 않은 부분들은 필요할때만 메모리에 올려 사용하게 된다. 이때 메모리에 상주하는 운영체제의 핵심 부분을 커널이라고 한다.

이러한 IPC 기법에는 크게 2가지 방식이 존재한다.

<img width="542" alt="스크린샷 2022-11-04 02 41 49" src="https://user-images.githubusercontent.com/67703882/199795456-3f434a23-5200-4265-aaad-d89291ee10ea.png"  >

- Shared Memory 방식

  - 프로세스의 일부 주소 공간을 공유 메모리로 설정하여, 프로세스끼리 메모리을 공유한다.
  - 공유한 메모리 영역에 읽기 및 쓰기를 통해서 통신을 수행한다.

- Message Passing 방식

  - 프로세스 간 메모리 공유 없이, API를 통해 송/수신자 간 메세지를 주고 받는다.

  - 커널은 메세지 큐를 사용하여 메세지를 관리한다.

  - ex. 파이프, TCP/IP 소켓

## 참고

https://velog.io/@raejoonee/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%8A%A4%EB%A0%88%EB%93%9C%EC%9D%98-%EC%B0%A8%EC%9D%B4

https://charlezz.medium.com/process%EC%99%80-thread-%EC%9D%B4%EC%95%BC%EA%B8%B0-5b96d0d43e37

https://velog.io/@yanghl98/OS%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C-IPC%EB%9E%80
