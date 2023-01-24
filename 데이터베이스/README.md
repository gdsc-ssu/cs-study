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

<details>
<summary><strong>💡 데이터베이스의 설계 순서</strong></summary>
  <ol>
    <li>요구 분석</li>
    <ul>
      <li>요구 조건 명세서 작성</li>
    </ul>
		<li>개념적 설계</li>
    <ul>
      <li>개념 스키마, 트랜잭션 모델링, E-R 모델</li>
    </ul>
    <li>논리적 설계</li>
    <ul>
      <li>dbms에 맞는 스키마 설계, 트랜잭션 인터페이스 설계</li>
    </ul>
    <li>물리적 설계</li>
    <ul>
      <li>dbms에 맞는 물리적 구조 구축</li>
    </ul>
    <li>구현</li>
    <ul>
      <li>dbms로 데이터 생성 및 트랜잭션 작성</li>
    </ul>
  </ol>
</details>

<details>
<summary><strong>💡 키의 종류</strong></summary>
  <ul>
    <li>슈퍼키(Super Key)</li>
    <ul>
      <li>유일성을 만족하는 키</li>
    </ul>
		<li>후보키(Candidate Key)</li>
    <ul>
      <li>유일성과 최소성을 만족하는 키</li>
    </ul>
    <li>기본키(Primary Key)</li>
    <ul>
      <li>후보키에서 선택된 키</li>
    </ul>
    <li>대체키(Alternate Key)</li>
    <ul>
      <li>후보키 중에 기본키로 선택되지 않은 키</li>
    </ul>
    <li>외래키(Foreign Key)</li>
    <ul>
      <li>다른 릴레이션의 기본키가 되는 키</li>
    </ul>
  </ul>
</details>

<details>
<summary><strong>💡 유일성과 최소성</strong></summary>
  <ul>
    <li>유일성: 하나의 키 값으로 튜플을 유일하게 식별할 수 있는 성질</li>
    <li>최소성: 키를 구성하는 속성들 중 꼭 필요한 최소한의 속성들로만 키를 구성하는 성질
  </ul>
</details>
<details>
<summary><strong>💡 인덱스란 무엇인지</strong></summary>
추가적인 쓰기 작업과 저장 공간을 활용해 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조<br>
인덱스는 책의 맨 처음 또는 맨 마지막에 있는 색인을 의미
  <ul>
    <li>index : 색인</li>
    <li>데이터 : 책의 내용</li>
    <li>데이터가 저장된 레코드 주소 : 인덱스 목록에 있는 페이지 번호</li>
  </ul>
</details>

<details>
<summary><strong>💡 INNER JOIN vs OUTER JOIN</strong></summary>
  <ul>
    <li><strong>INNER JOIN</strong></li>
    결합된 테이블에 조건의 내용이 공통으로 들어가 있는 값을 결과 집합으로 만들어준다. ON 다음에 들어가는 조건에 맞는 내용들만 보여주게 된다.
    <li><strong>OUTER JOIN</strong></li>
    INNER JOIN 문을 포함하고 한쪽에만 내용이 있더라도 지정한 기준 테이블에 있는 모든 데이터를 가져오는 조인방식
  </ul>
  ⇒ INNER JOIN은 교집합, OUTER JOIN은 합집합
</details>