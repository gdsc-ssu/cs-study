# CPU Scheduling

: 다음에 실행할 프로세스를 정하는 **스케줄링 정책(scheduling policy)**

<br>

## 기본 정보

### 분류

기본적으로 스케줄링은 아래 두 가지로 분류된다.

- **Non-preemptive scheduling (비선점 스케줄링)**
  - 프로세스가 실행되면 해당 프로세스가 종료되거나 양보할 때까지 계속 실행
  - 협력적으로 동작해야함 (안그러면 하나가 독점함!)

- **Preemptive scheduling (선점형 스케줄링)**
  - 프로세스 실행 도중에도 **OS가 interrupt로 개입** 가능
  - 대부분 이 방식 사용

<br>

### 용어

- **Workload**: CPU에서 실행될 작업들의 description (개별: work, 집합: workload)
- **Metric**: 성능 지표 (스케줄링 퀄리티)
- **Scheduler**: 다음에 어떤 프로세스를 실행할지 정의된 로직

<br>

### 워크로드에 대한 가정 (Workload Assumptions)

스케줄링 이론 학습을 위해 아래와 같은 가정들을 두고 시작한다.

1. 각각의 계산 작업들이 동일한 시간만큼 실행된다.
2. 모든 작업들이 동일한 시간에 도착한다.
3. 한번 실행을 시작하면 연산이 끝날 때까지 할당받은 시간동안 계속 계산한다.
4. 각각의 job들은 CPU 연산만 사용한다.
5. 각각의 job들의 실행시간은 알려져 있다.

<br>

### 스케줄링 평가항목 (Scheduling Metrics)

1. **반환 시간(turnaround time) = 작업이 완료된 시점 - 도착 시점**
2. **공정성 (fairness)**

3. **응답 시간(response time) = 처음 스케줄된 시점 - 도착 시점**

<br>

## 방법1. FIFO Scheduling (First In First Out, FCFS)

: job이 도착한 순서대로 스케줄링

<br>

### 장점

- 구현이 쉬움
- 위에서 정의한 가정 내에서는 매우 잘 동작함 (하지만 현실에서는 위 가정들이 보장되지 않는다)

- **no starvation**



### 단점

- Non-preemptive
- 각각의 job들의 실행시간이 다른 경우, 성능이 매우 떨어져 비효율적이다.

<br>

### 예제

#### 예제1)

- 조건

  - 도착) A, B, C 순으로 0초 (거의 동시에)

  - 실행시간) 각각 10초동안


- 결론

  <img width="369" alt="image" src="https://user-images.githubusercontent.com/70627979/161374035-80c691d3-2cd1-48cd-939f-c9b9901fd61e.png">

  - Tt(A) = 10 - 0

  - Tt(B) = 20 - 0

  - Tt(C) = 30 - 0

  - **Average turnaround time** = (10 + 20 + 30) / 3 = 20sec

    **(Tt는 turnaround time 계산값)**




#### 예제2)

위 단점에서 말했던 것처럼, 가정1을 완화시켜 각각의 job들의 실행시간이 다른 경우에는 성능이 매우 떨어져 비효율적이게 된다.

- 조건

  - 도착) A, B, C 순으로 0초 (거의 동시에)

  - 실행시간) A: 100초, B,C: 10초


- 결론

  <img width="393" alt="image" src="https://user-images.githubusercontent.com/70627979/161374070-13216076-b3f0-4ceb-9408-479e8353959f.png">

  - Tt(A) = 100 - 0

  - Tt(B) = 110 - 0

  - Tt(C) = 120 - 0

  - **Average turnaround time** = (100 + 110 + 120) / 3 = 110sec


<br>

## 방법2. SJF Scheduling (Shortest Job First)

: 실행시간이 가장 짧은 job부터 실행

<br>

### 장점

- 실행시간이 달라도 turnaround time 측면에서 나쁘지 않음



### 단점

- **Non-preemptive**
- **도착시간이 달라지면 FIFO와 비슷한 성능**을 가짐

<br>

### 예제

#### 예제1)

FIFO 예제2와 동일한 조건이 주어진다고 했을 때, 실행시간이 짧은 B,C 부터 먼저 실행되어 성능이 향상된다.

- 조건

  - 도착) A, B, C 순으로 0초 (거의 동시에)

  - 실행시간) A: 100초, B,C: 10초


- 결론

  <img width="449" alt="image" src="https://user-images.githubusercontent.com/70627979/161374573-7f0be623-1f8e-426a-a61c-40311a6a0622.png">

  - Tt(A) = 120 - 0

  - Tt(B) = 10 - 0

  - Tt(C) = 20 - 0

  - **Average turnaround time** = (10 + 20 + 120) / 3 = 50sec




#### 예제2)

하지만 가정2를 완화시켜 도착시간이 달라지게되면 FIFO와 비슷한 성능을 갖게된다.

- 조건

  - 도착) A: 0초, B,C: 10초 (거의 동시에), 

  - 실행시간) A: 100초, B,C: 10초


- 결론

  <img width="402" alt="image" src="https://user-images.githubusercontent.com/70627979/161374749-79f18ffc-cc25-42a1-bdfd-d8a6ad01ed89.png">

  - Tt(A) = 100 - 0

  - Tt(B) = 110 - 10

  - Tt(C) = 120 - 10

  - **Average turnaround time** = (100 + 100 + 110) / 3 = 103.33sec


<br>

## 방법3. STCF Scheduling (Shortest Time-to-Completion First)

: 남은 실행시간이 가장 짧은 job부터 실행

- **SJF 스케줄러 방식에 선점형 방식을 추가**한 것이다. (가정3 완화)

- 새로운 job이 도착하면 시스템에 존재하는 job과 새로 들어온 job의 남은 실행시간을 비교하여 적게 남은 것을 선택한다.

- PSJF(Preemptive Shortest Job First)으로도 알려져 있다.

<br>

### 장점

- **preemptive**



### 단점

- 작업의 길이를 미리 알고, job이 CPU만 사용하며, 평가기준이 turnaround time 하나일 때만 STCF가 문제 없다.

<br>

### 예제

- 조건

  - 도착) A: 0초, B,C: 10초 (거의 동시에)

  - 실행시간) A: 100초, B,C: 10초

- 결론

  <img width="400" alt="image" src="https://user-images.githubusercontent.com/70627979/161375096-f68ed6ae-3806-4fd4-9d20-e9dd3487165f.png">

  - Tt(A) = 120 - 0

  - Tt(B) = 20 - 10

  - Tt(C) = 30 - 10

  - **Average turnaround time** = (120 + 10 + 20) / 3 = 50sec


<br>

## 방법4. RR Scheduling (Round Robin)

: 시간을 잘게 쪼개어 순서대로 번갈아가면서 실행

- FIFO, SJF, STCF 스케줄링 방식들은 모두 **response time** 측면에서 별로이다.
  (응답 시간(response time) = 처음 스케줄된 시점 - 도착 시점)
- circular FIFO queue 라고도 불림

<br>

### time-slice length

- **shorter**
  - better response time
  - context switching이 너무 자주 일어나 오버헤드가 심해져 전체 시스템 성능이 저하됨
- **longer**
  - worse response time

<br>

### 장점

- **Preemptive**
- **No starvation**
- **good response time**



### 단점

- **bad turnaround time**

<br>

### 예제

SJF/STCF vs RR

- 조건

  - 도착) A,B,C: 0초 (거의 동시에)

  - 실행시간) A,B,C: 5초


- 결론

  <img width="550" alt="image" src="https://user-images.githubusercontent.com/70627979/161376264-485d2e4c-0e11-43e2-833a-126efcdbf915.png" style="zoom:67%;" >

  - SJF/STCF

    - **T(average response)** = (0 + 5 + 10) / 3 = 5sec

    - **T(average turnaround)** = (5 + 10 + 15) / 3 = 10sec


  - RR (time-slice of 1sec)

    - **T(average response)** = (0 + 1 + 2) / 3 = 1sec (good)

    - **T(average turnaround)** = (13 + 14 + 15) / 3 = 14sec (bad)


<br>

## I/O가 있는 경우 (Incorporating I/O)

가정 4를 완화시켜, I/O가 있다고 하고 **STCF**를 적용시켜보자.

- job이 I/O request 시작 시
  - 해당 job block
  - 다른 job 스케줄됨
- job이 I/O 끝났을 시
  - interrupt 올림
  - 이후에 policy에 의해서 어떤 job을 실행할지 결정

<br>

### 예제

중첩이 있을 때와 없을 때를 비교

- 조건

  - 도착) A,B: 0초 (거의 동시에)

  - 실행시간) A,B: 50ms

  - 추가) A: 10ms마다 I/O request (A는 10ms만 실행하는 것처럼 스케줄러 작성)


- 결론

  - 중첩이 없는 경우

    <img width="447" alt="image" src="https://user-images.githubusercontent.com/70627979/161377231-ab173f63-2f26-417a-a77c-d6382c2abe33.png">

    → turnaround time, response time 둘 다 별로


  - **중첩이 있는 경우**

    <img width="428" alt="image" src="https://user-images.githubusercontent.com/70627979/161377173-98620630-4f83-4d60-a5f5-f07d252de391.png">

    → 훨씬 효율적이다.




<br>

## 방법5. MLFQ

위에서 FIFO, SJF, STCF, RR 스케줄링 기법에 대해 알아봤다. 이 방식들의 한계점을 알아보고, 가장 인기있는 스케줄링 기법인 MLFQ에 대해 알아보자.

<br>

### MLFQ 요약

- Rule 1) Priority(A) > Priority(B) 이면, A가 실행된다.

- Rule 2) Priority(A) == Priority(B) 이면, A와 B는 RR 방식으로 실행된다.

- Rule 3) job이 시스템에 들어오면, 가장 높은 우선순위를 배정받음

- Rule 4) 특정 priority level에서 정해진 시간만큼 돌았으면, job의 priority를 1단계 낮춤

- Rule 5) 일정 기간(S) 지나면, 시스템의 모든 job들을 가장 높은 우선순위의 큐로 이동시킴


<br>

### Goals

- Optimize turnaround time

  : SJF, STCF는 실행시간을 미리 안다는 가정 필요하다.

- Minimize response time for interactive jobs

  : RR은 turnaround time 측면에서 나쁘다.

​	→ **사전 정보 없이, interactive jobs의 response time을 줄이면서, 동시에 turnaround time도 줄이는 방법**은 없을까?

​	→ workloads의 사전 정보 없이 스케줄링하려면, **실행하는 job이 어떤 특성을 갖는지 과거 경험을 통해 추정**해야 한다.

<br>

### MLFQ: Basic Rules

- MLFQ는 여러 개의 큐로 구성된다.
  - **Multi-Level Feedback Queue**
  - 각각의 큐마다 다른 우선순위를 가지고 있다.
- 어떤 하나의 job은 여러 큐 중 하나에 들어가야 한다.



> #### Rule 1: Priority(A) > Priority(B) 이면, A가 실행된다.
>
> #### Rule 2: Priority(A) == Priority(B) 이면, A와 B는 RR 방식으로 실행된다.

<br>

워크로드가 아래 두 가지로 구성된다고 가정해보자

- Interactive jobs

  - 런타임이 대체로 짧고, response time이 짧길 원함
  - CPU를 사용하는 시간이 짧고, 대부분의 시간을 I/O를 기다리는데 사용

  **→ high priority**

- CPU-intensive jobs

  - CPU를 오랫동안 사용
  - response time을 크게 신경쓰지 않음

  **→ low priority**

<img src="https://user-images.githubusercontent.com/70627979/162583297-18fc7569-f59e-4ca7-aed0-bd82da0c88bc.png" alt="image" style="zoom: 33%;" />

그러면 job이 어떤 종류인지는 어떻게 구분하는 것일까? **→ behavior(행동)을 보고 판단!**

<br>

### 1) 우선순위 변경

MLFQ 우선순위 결정 알고리즘)

> #### Rule 3: job이 시스템에 들어오면, 가장 높은 우선순위를 배정받음
>
> #### Rule 4a: 만약 job이 현재 priority에서 실행됐는데 할당된 time-slice를 전부 사용했다면, job의 priority를 1단계 낮춤
>
> #### Rule 4b: 만약 job이 현재 priority에서 실행됐는데 할당된 time-slice를 전부 사용하기 전에 CPU를 양보하면, 그 job은 동일한 priority를 유지함



### 예제

- A Single Long-Running Job

<img width="814" alt="image" src="https://user-images.githubusercontent.com/70627979/161436957-97fc7373-6062-4a41-90d9-591c8fad928b.png" style="zoom:67%;" >

- Along Came a Short Job (job A가 실행되는 도중 job B가 들어온 상황)

<img width="907" alt="image" src="https://user-images.githubusercontent.com/70627979/161437137-2407745f-2eac-4c01-add9-95930c7874d7.png" style="zoom:67%;" >

- I/O가 있는 경우

<img width="808" alt="image" src="https://user-images.githubusercontent.com/70627979/161437251-eebd8aac-00ac-495e-a9cd-1613d34fd093.png" style="zoom:67%;" >



<br>

#### Basic MLFQ의 문제점

- **Starvation**

  → 한 시스템에 interactive job들이 너무 많이 존재하면, 낮은 우선순위를 갖는 CPU-intensive job들은 아예 스케줄을 못받는다.

- **Game the scheduler**

  → 앱 개발자가 스케줄러를 속여서 자기 앱만 계속 실행되게 악용할 수 있다. (99%의 time-slice 사용) 

- **A program may changes its behavior over time**

  → 프로그램의 behavior(행동)이 바뀌었음에도 이를 반영하지 못할 수 있다.
  (e.g. 처음엔 CPU 많이 쓰다가, 이후엔 적게 쓰는 것으로 전환되는 경우)

<br>

### 2) The Priority Boost (우선순위 상향 조정)

starvation 문제를 해결하기 위해 룰을 추가하였다.

> #### Rule 5: 일정 기간(S) 지나면, 시스템의 모든 job들을 가장 높은 우선순위의 큐로 이동시킴

<img width="857" alt="image" src="https://user-images.githubusercontent.com/70627979/161437677-f7c2b18f-e282-4040-8b7f-ad64cdbdba05.png" style="zoom: 67%;" >

<br>

### 3) Better Accounting (더 나은 시간 측정)

스케줄러 악용 문제를 해결하고자 4번째 룰을 개선하였다.

> #### Rule 4: 특정 priority level에서 정해진 시간만큼 돌았으면, job의 priority를 1단계 낮춤

→ 각 priority level에서 최대 사용 시간 제한!

<img width="904" alt="image" src="https://user-images.githubusercontent.com/70627979/161437993-defa546f-ab82-4e50-876d-abe23e29037b.png" style="zoom:67%;" >

<br>

### Tuning MLFQ and Other Issues

- 높은 우선순위 큐 → 짧은 slice-time
- 낮은 우선순위 큐 → 긴 slice-time



<br>

## RT (Real-Time)

### CPS

: Cyber-physical systems (물리적 요소 + 사이버/컴퓨팅적 요소)

<br>

### Requirements

- **Safety**
  - 시스템이 동작하는 타이밍이 정확히 맞아떨어져야함
- Performance
- Interoperability

<br>

### Real-Time Systems

- 논리적 정확성 + 시간적 정확성
- before deadlines
- Real-time != fast (**predictable**이 더 중요!)

<br>

### Performance measure

- deadline에 얼마나 잘 맞춰줄 수 있는지

<br>

### Types

- **Hard real-time systems**: 하나라도 데드라인 못맞추면 결과가 치명적인 시스템
  - Validation(검증) 필수
  - 어떤 상황에도 데드라인 100% 지켜야함 
- **Soft real-time systems**: deadline miss가 크게 치명적이지 않은 시스템

<br>

## Real-time scheduling

### Real-time task

- Task: 여러 개의 비슷한 작업(jobs)
  - Period **p**: 주기
  - Execution time **e**: 실행 시간

<br>

### 성능 지표 (Performance metric)

: **Real-time schedulability**

→ 모든 task가 데드라인을 맞출 수 있는지

<br>

## 방법6. RM (Rate Monotonic)

: 주기(period)가 짧을수록 높은 우선순위 가짐

<br>

### 문제점

- deadline을 못맞추는 문제가 발생

  <img width="818" alt="image" src="https://user-images.githubusercontent.com/70627979/163714403-86e5fed2-68e6-4215-976e-cb3da29b5c11.png" style="zoom:50%;" >

<br>

### RT (Response Time)

**real-time OS에서는 일반적인 OS와는 다른 방법의 Response Time 계산법을 갖는다**.

Response Time 계산

- **일반 OS**: 처음 스케줄링 된 시간 - 도착 시간
- **real-time OS**: **끝나는 시간 - period job이 생기는 시간**

<br>

### RM - Analysis

#### RTA (Response Time Analysis)

: 만약 모든 task의 response time <= period(==deadline)인 경우, RM 스케줄러로 스케줄링 가능

<br>

#### Utilization bound

: 만약 모든 task의 ΣUi <= n*(2^(1/n) - 1)인 경우, RM 스케줄러로 스케줄링 가능

- Ui = ei / pi

<br>

## 방법7. EDF (Earliest Deadline First)

: deadline이 가장 임박할수록 높은 우선순위 가짐

<img width="816" alt="image" src="https://user-images.githubusercontent.com/70627979/163714754-c592ebaf-a15b-48c3-a02e-4ed2dec0aaaa.png" style="zoom: 75%;" >

<br>

### EDF - Analysis

#### DBF (Demand Bound Function)

- Demand Bound Function: dbt(t) → t 동안 필요한 프로세스 양이 얼마나 되는지

- 만약 모든 interval **t** 에 대해 dbf(t) <= t 를 만족하는 경우, EDF 스케줄러로 스케줄링 가능

<br>

#### Utilization bound

- 만약 모든 task의 ΣUi <= 1 인 경우, EDF 스케줄러로 스케줄링 가능

  → Utilization Bound가 1이라는 것은 특정 시간동안 CPU를 계속 사용가능하다는 것

<br>

### RM vs EDF

#### Rate Monotic

- 쉬운 구현
- 우선순위가 높은 tasks는 대체로 Predictability가 높다.
  - Predictability: deadline을 얼마나 잘 맞춰줄 수 있는지

#### EDF

- CPU를 한순간도 쉬지 않게 거의 꽉 채워서 사용 가능
- 컴퓨팅 능력에 비해 task들이 더 많이 들어온 경우, 잘 동작하지 않는다.

<br>

## 참고 자료

- [Operating Systems: Three Easy Pieces](https://github.com/remzi-arpacidusseau/ostep-translations/tree/master/korean)
