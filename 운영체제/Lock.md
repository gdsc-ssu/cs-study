# Lock

OS의 핵심인 동시성(Concurrency)의 중요 개념 중 하나인 Lock에 대해 알아보자



## 1. Lock이 필요한 이유

Lock은 프로세스 또는 스레드들이 수행되는 시점을 조절하여 서로가 알고 있는 정보가 일치하는 **Synchronization**(동기화)를 위해 필요하다.

그러면 Synchronization(동기화)은 왜 필요할까? 그 이유를 알기 위해서는 Shared Resources(공유 자원)과 관련 개념들에 대한 이해가 필요하다.

<br>

### 1.1 Sharing Resources (공유 자원)

- **Local variables**(지역 변수)는 스레드끼리 공유되지 않는다.
  - Local variables(지역 변수)는 스택에 저장되고, 각 스레드는 고유한 스택을 보유하기 때문이다.
  - 스택에 대한 포인터를 주고받는 것이 가능하지만, 절대 하면 안된다.
- **Global variables**(전역 변수)는 static data segment에 저장되기 때문에 스레드간 공유가 가능하다.
- **Dynamic objects**(동적인 객체)는 heap에 저장되기 때문에 스레드간 공유가 가능하다. 

- 프로세스들은 메모리 공유가 가능하다 (shmem)

<br>

### 1.2 Synchronization Problem

두 개 이상의 동시에 실행되는 스레드가 공유 자원에 접근하여 **race condition**을 만들어내고, 동일한 프로그램을 실행하여도 다른 결과가 도출될 수 있다.

그래서 공유 자원의 접근을 위한 **synchronization mechanism**이 필요한 것이다.

<br>

## 2. Lock의 역할

위에서 Lock은 Synchronization(동기화)를 위해 필요하다고 하였다. 그러면 Lock이 정확히 어떻게 동작하여 Synchronization(동기화)을 보장해줄 수 있는 것일까?

**→ Lock은 Critical Section(임계 영역)이 하나의 atomic instruction인 것처럼 동작하도록 도와준다.**

<br>

새로운 개념 Critical Section(임계 영역)이 등장했다. 무엇인지 알아보자.

### 2.1 Critical Section (임계 영역)

Critical Section은 **공유 자원에 접근하는 instructions의 집합**으로, **Mutual Exclusion(상호 배제)을 보장**해야 한다.

- 보장하는 방법

  - 어떤 한 시점에 **하나의 스레드만 Critical Section 실행**

  - **atomic**하게 실행

  - 다른 스레드는 Critical Section의 시작점에서 대기

  - 실행이 끝나야만 대기중이던 스레드가 진입 가능

> Mutual Exclusion (상호 배제): 동시에 Critical Section(임계 영역)에 진입하는 것을 방지하기 위해 사용되는 알고리즘

<br>

## 3. Requirements for Locks

- **Correctness**

  - **Mutual Exclusion**

    : 한 번에 오직 하나의 스레드만 critical section에 진입해야함

  - **Progress (deadlock-free)**

    : 여러 개의 스레드가 동시에 진입하려 했을 때, 1개는 진입해야함

  - **Bounded waiting (starvation-free)**

    : 언젠가는 잡을 수 있어야함 

- **Fairness**

- **Performance**

  - lock을 구현하기 위해 CPU를 얼마나 쓸 것인지

<br>

## 4. 동작 방식

Lock은 Critical Section이 하나의 atomic instruction인 것처럼 되도록 도와주기 위해 다음과 같이 동작한다.

- Lock variable은 해당 lock의 상태를 담고 있다.
  - **available**
  - **acquired**
- 최대 1개의 스레드만 lock을 잡을 수 있다.

<br>

### 4.1 The semantics of the `lock()`

- `lock()`
  1. try to acquire the lock

  2. 만약 어느 스레드도 lock을 잡고 있지 않으면, 스레드는 lock을 잡음
  3. critical section에 진입
  4. 다른 스레드들은 critical section에 진입하는 것이 막힌다.

- `unlock()`
  1. lock의 주인이 unlock()을 호출하면, lock은 available 상태로 변함
  2. lock()에서 대기중이던 스레드를 깨움

<br>

## 5. Lock의 활용

### Mutex

: 한 프로세스(스레드)에 의해 소유될 수 있는 Key를 기반으로 한 Mutual Exclusion(상호 배제) 기법

<br> 

### Semaphore

: 현재 공유 자원에 접근할 수 있는 프로세스(스레드)의 수를 나타내는 값을 두어 Mutual Exclusion(상호 배제)을 달성하는 기법

<br>

[여기](https://worthpreading.tistory.com/90)에 나와있는 화장실 예제가 Mutex와 Semaphore를 이해하기 더 좋은 것 같아서 공유합니다!

<br>

## 참고 자료

- [Operating Systems: Three Easy Pieces](https://github.com/remzi-arpacidusseau/ostep-translations/tree/master/korean)
- https://worthpreading.tistory.com/90