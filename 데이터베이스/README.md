# 데이터베이스

<details>
<summary><strong>💡 트랜잭션이란 무엇인지</strong></summary>
  <ul>
    <li>
      트랜잭션이란 데이터베이스의 상태를 변환시키는 하나의 논리적인 작업 단위를 구성하는 연산들의 집합이다. (ex. 계좌 이체 등)
    </li>
    <li>
    	하나의 트랜잭션은 무조건 commit 되거나 rollback 된다.
    </li>
    <ul>
      <li>
      	트랜잭션에 대한 작업이 성공적으로 종료되어 데이터베이스가 다시 일관된 상태에 있을 때 commit 된다. 
      </li>
      <li>
      	트랜잭션 처리가 비정상적으로 종료되어 데이터베이스의 일관성을 깨트렸을 때, 트랜잭션의 일부가 정상적으로 처리되었더라도 트랜잭션의 원자성을 유지하기 위해 트랜잭션이 행한 모든 연산을 취소하는 rollback 작업을 한다.
      </li>
    </ul>
    <li>
    	데이터베이스의 응용 프로그램은 트랜잭션의 집합이라고 정의할 수 있다. 
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 트랜잭션의 성질(ACID)이란</strong></summary>
  <ul>
    <li>원자성(Atomicity)</li>
    <ul>
      <li>트랜잭션의 모든 연산들은 정상적으로 수행 완료되거나 아니라면 어떠한 연산도 수행되지 않은 상태를 보장해야한다. </li>
    </ul>
		<li>일관성(Consistency)</li>
    <ul>
      <li>트랜잭션이 완료된 후에도 데이터베이스가 일관된 상태로 유지되어야한다.</li>
    </ul>
    <li>독립성(Isolation)</li>
    <ul>
      <li>하나의 트랜잭션이 실행 도중에 변경한 데이터는 이 트랜잭션이 완료될때까지 다른 트랜잭션이 참조할 수 없다. </li>
    </ul>
    <li>지속성(Durability)</li>
    <ul>
      <li>성공적으로 수행된 트랜잭션은 영원히 반영되어야한다. </li>
    </ul>
  </ul>
</details>