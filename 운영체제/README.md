# 운영체제

<details>
<summary><strong>💡 프로세스의 5가지 상태</strong></summary>
  <ul>
    <li>New(생성) : 프로세스가 생성된 상태, PCB를 할당받은 상태</li>
    <li>Running(수행) : 프로세스가 CPU에 할당되어 실행 중인 상태</li>
    <li>Ready(준비) : 프로세스가 CPU에 할당되기를 기다리는 상태</li>
    <li>Waiting(대기/블록) : 보류(block) 상태라고도 함, 프로세스가 입출력이나 이벤트를 기다리는 상태</li>
    <li>Exit(종료) : 프로세스 종료 상태</li>
    <img src="https://user-images.githubusercontent.com/70627979/210798300-49b1a731-6c4f-4500-a296-16c7e4a9a7f2.png"/>
  </ul>
</details>

<details>
<summary><strong>💡 프로세스와 스레드의 차이</strong></summary>
  <ul>
    <li>
      프로세스 : 메모리 상에서 실행중인 프로그램
      <br>
      프로세스는 최소 하나의 스레드를 보유하고 있으며, 각각 별도의 주소 공간을 독립적으로 할당받음. (<code>code</code>, <code>heap</code>, <code>stack</code>)
    </li>
    <li>
    	스레드 : 프로세스 내에서 실행되는 흐름 단위
      <br>
      스레드는 code, heap, stack 의 주소공간 중 stack 만 별도로 할당받으며 나머지 영역은 스레드끼리 서로 공유함.
    </li>
	</ul>
</details>

<details>
<summary><strong>💡 동기와 비동기의 차이</strong></summary>
  <ul>
    <li>
      동기 : 어떤 일이 끝난 후에 다음 일을 하는 것
      <ul>
        <li>system call이 끝날 때까지 기다리고 결과물(반환 값)을 가져옴.</li>
      </ul>
    </li>
    <li>
      비동기 : 어떤 일이 끝나지 않아도 다음 일을 수행하는 것
      <ul>
        <li>system call이 완료되지 않아도 기다리지 않으며, 추후 완료될 때 결과물(반환 값)을 가져옴.</li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 데드락의 발생 조건</strong></summary>
  여러개의 프로세스들이 여러가지 이유로 서로의 작업이 끝나기만을 기다리며 생기는 교착상태.
  <ul>
    <li>
      Mutual Exclusion (상호배제) : 서로 다른 프로세스가 critical section에 동시에 진입할 수 없는 것.
    </li>
    <li>
    	Hold & wait : 자원을 최소한 하나를 점유하고, 다른 쓰레드가 사용중인 자원을 사용하기 위해 기다림.
    </li>
    <li>
    	No preemption (비선점) : 비선점형 스케쥴러를 사용할 때. (critical section에 강제로 진입 불가능)
    </li>
    <li>
    	circular wait (순환대기) : 대기하고 있는 프로세스들이 순환 형태로 대기하고 있을 때
    </li>
  </ul>
  ⇒ 4가지를 전부 만족해야 한다.
</details>