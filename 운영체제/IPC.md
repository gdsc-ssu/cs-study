# IPC

## IPC(InterProcess Communication) 란?

IPC 란 Process 들 간에 데이터 및 정보를 주고 받기 위한 메커니즘으로, Kernel 에서 IPC 를 위한 도구를 System Call 의 형태로 제공한다. 

Process는 기본적으로 독립되어 존재하기 때문에 서로 간의 통신이 어렵다는 문제가 있다. 이러한 Process 간 협력 모델(Cooperating Process Model)을 구현하기 위해서는 IPC가 필요하다. 

## IPC 모델 

IPC 에는 Shared Memory 와 Message Passing 로 2가지 모델이 존재한다. 

<img src="https://user-images.githubusercontent.com/67703882/203753478-820f176a-8a38-4af1-b38e-0f06283bfd93.png" alt="image" style="zoom:67%;" />

#### Share Memory 

- Process 의 특정 메모리 영역을 공유한다. 공유 메모리 영역에 Read 와 Write 를 통해 통신을 수행한다. 
- 응용 프로그램 레벨에서 통신 기능을 제공한다. 즉, 공유 메모리가 한번 설정되면, 그 이후의 통신은 Kernel의 관여 없이 진행 가능하다.
- 메모리 영역에 대한 여러 프로세스들의 **동시적 접근을 제어**하기 위한 방법이 필요하다. 동기화를 위한 접근 제어 방식에는 Locking 이나 Semaphore 방법 등이 있다. 
- 구현 IPC : Shared Memory

#### Message Passing

- Process 간 메모리 공유 없이, 고정 혹은 가변 길이의 메세지를 송/수신자끼리 주고 받는다. -> Send/Receive 방식
- Kernel 단에서 관리된다. 즉 Kernel 을 경유하여 메세지를 주고 받고, Kernel 에서 데이터를 버퍼링하기도 한다.
- Send 와 Receive 를 수행할때 Kernel이 동기화를 제공하기 때문에, 프로그램에서 동기화에 대한 고려 없이 사용이 가능하다. 그러나 실행중이지 않은 프로세스가 메세지를 수신하는 상황 등 Context Switching 와 관련하여 고려할 부분이 존재한다. 
- 구현 IPC : Pipe, Message Queue, Socket 

## IPC 종류 

#### Pipe

<img width="335" alt="스크린샷 2022-11-24 18 59 19" src="https://user-images.githubusercontent.com/67703882/203754637-0f0b594e-94e4-4289-b8ab-7270e3c183b3.png">

Pipe는 하나의 프로세스가 다른 프로세스로 데이터를 직접 전달하는 방법이다. 

- 파이프 내 데이터는 한 쪽 방향으로만 이동할 수 있기 때문에, 양방향 통신을 위해서는 2개의 파이프가 필요하다.
- 보내진 순서대로만 받을 수 있고, 용량 제한이 있기 때문에 파이프가 꽉차면 더이상 사용할 수 없다. 
- 기존의 Pipe 방식은 부모-자식 프로세스간 통신 방법이었지만, 일반 프로세스끼리 사용되는 Pipe 방식도 존재한다. 

#### Signal 

<img width="218" alt="스크린샷 2022-11-24 19 15 34" src="https://user-images.githubusercontent.com/67703882/203758301-0051ba54-63d2-44be-8d1a-03e042b06616.png"  >

Signal은 특정 프로세스가 Kernel을 통해 Event를 전달하는 방법이다. 

- 송신 프로세스는 여러 신호 중 하나를 특정 프로세스에 보내고, 이러한 동작은 수신 프로세스의 상태와 무관하게 수행된다. 

- 수신 프로세스는 신호 종류에 따라 신호 처리 방법을 지정할 수 있다. 

  - 그냥 무시한다

  - 단순히 신호를 붙잡아 둔다. (붙잡아 두었다가 나중에 처리하는 등)

  - 특정 처리 루틴(Signal Handler)를 두어서 처리한다. 

- 송수신이 언제든지 이루어질 수 있기 때문에 비동기적인 동작이 가능하다. 단, 주의할 점은 수신 프로세스가 Scheduling 되어 실행 중일때만 수신한 Signal을 처리할 수 있다. 

#### Shared Memory

<img width="338" alt="스크린샷 2022-11-24 19 24 52" src="https://user-images.githubusercontent.com/67703882/203760373-336d1751-80ac-45b1-8150-ef4b1d6b73e6.png">

Shared Memory는 두개 이상의 프로세스들이 하나의 메모리 영역을 공유하여 통신하는 방법이다. 

- 공유 메모리 영역을 직접 사용하기 때문에 빠르고 자유로운 통신이 가능하다. 
- 그러나 둘 이상의 프로세스가 동시에 메모리 데이터를 변경하지 않도록 프로세스 간 동기화가 필요하다.

#### Message Queue

<img width="451" alt="스크린샷 2022-11-24 19 25 07" src="https://user-images.githubusercontent.com/67703882/203760424-15f33403-e884-494b-aad9-479a4d4f9f4c.png" style="zoom:80%;" >

Message Queue는 고정된 크기를 갖는 메세지의 연결 리스트(Linked List)를 이용하여 통신을 하는 방법이다. 

- Message 단위의 단방향 통신 

- 메세지의 형태는 통신하고자 하는 프로세스 간의 약속이 필요하다. 따라서 메세지의 형태를 사용자가 정의하여 사용한다. 
- 여러 프로세스가 동시에 Queue 접근이 가능하므로 동기화를 위한 작업이 필요하다.

#### Socket 

<img width="443" alt="스크린샷 2022-11-24 19 26 25" src="https://user-images.githubusercontent.com/67703882/203760714-d498832e-635b-4d71-ae49-24682071bf05.png">

소켓 통신은 흔히 네트워크 통신 기법으로 많이 사용되는 방식으로, 데이터 교환을 위해 양쪽 PC에서 각각 임의의 Port를 정하고 해당 Port 간의 대화를 통해 데이터를 주고 받는 방식이다. 

- Port 번호를 이용해 통신하려는 상대 Process 의 Socket을 찾아간다. 
- 다른 IPC 방법과 달리 Machine Boundary 에 구애 받지 않는다. 즉 Port 번호와 PC의 IP 주소를 조합하여 원격 통신이 가능해졌다. 
- 연결 방식에 따라 TCP(Reliable) / UDP(Unreliable) 통신으로 나눌 수 있다. 

## 참고

https://bluemoon-1st.tistory.com/22
