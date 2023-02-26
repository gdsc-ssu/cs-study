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
    <li>
      요구 분석
      <ul>
	      <li>요구 조건 명세서 작성</li>
  	  </ul>
    </li>
		<li>
      개념적 설계
      <ul>
	      <li>개념 스키마, 트랜잭션 모델링, E-R 모델</li>
  	  </ul>
    </li>
    <li>
      논리적 설계
      <ul>
	      <li>dbms에 맞는 스키마 설계, 트랜잭션 인터페이스 설계</li>
  	  </ul>
    </li>
    <li>
      물리적 설계
      <ul>
	      <li>dbms에 맞는 물리적 구조 구축</li>
  	  </ul>
    </li>
    <li>
      구현
      <ul>
	      <li>dbms로 데이터 생성 및 트랜잭션 작성</li>
  	  </ul>
    </li>
  </ol>
</details>

<details>
<summary><strong>💡 키의 종류</strong></summary>
  <ul>
    <li>
      슈퍼키(Super Key) : 유일성을 만족하는 키
    </li>
		<li>
      후보키(Candidate Key) : 유일성과 최소성을 만족하는 키
    </li>
    <li>
      기본키(Primary Key) : 후보키에서 선택된 키
    </li>
    <li>
      대체키(Alternate Key) : 후보키 중에 기본키로 선택되지 않은 키
    </li>
    <li>
      외래키(Foreign Key) : 다른 릴레이션의 기본키가 되는 키
    </li>
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

<details>
<summary><strong>💡 정규화란 무엇인가?</strong></summary>
  RDB(관계형 데이터베이스)에서 중복의 최소화를 위해 데이터를 구조화하는 작업이다.<br>
  중복된 데이터를 허용하지 않음으로써 데이터의 무결성(Integrity) 유지와 DB 저장 용량을 줄일 수 있다.<br>
  정규화는 나쁜 릴레이션의 어트리뷰트를 나눠 좋고 작은 릴레이션으로 분해하는 작업을 말한다.<br>
  정규화 작업을 통해 정규형을 만족하게 되며, 정규형은 특정 조건을 만족하는 릴레이션의 스키마 형태를 의미한다.<br><br>
  정규형에는 기본 정규형과 고급 정규형이 있다.
  <ul>
    <li>기본 정규형 : 제 1 정규형, 제 2 정규형, 제 3 정규형, BCNF(보이스/코드 정규형)</li>
    <li>고급 정규형 : 제 4 정규형, 제 5 정규형</li>
  </ul>
</details>

<details>
<summary><strong>💡 기본 정규형과 고급 정규형</strong></summary>
  <ul>
    <li>
      기본 정규형
      <ul>
      	<li>제 1 정규형 : 릴레이션에 속한 모든 속성의 도메인이 더 이상 분해되지 않는 원자 값으로만 구성된 정규형</li>
      	<li>제 2 정규형 : 릴레이션이 제 1 정규형에 속하고, 기본키가 아닌 모든 속성이 기본키에 완전 함수 종속된 정규형</li>
      	<li>제 3 정규형 : 릴레이션이 제 2 정규형에 속하고, 기본키가 아닌 모든 속성이 기본키에 이행적 함수 종속이 되지 않는, 이행적 함수 종속을 제거한 정규형</li>
      	<li>BCNF(보이스/코드 정규형) : 릴레이션의 함수 종속 관계에서 모든 결정자가 후보키인 정규형 후보키가 아닌 결정자를 제거함으로써 조건 성립</li>
    	</ul>
    </li>
		<li>
      고급 정규형
      <ul>
      	<li>제 4 정규형 : 릴레이션이 BCNF를 만족하며, 함수 종속이 아닌 다치 종속을 제거해야 만족하는 정규형</li>
      	<li>제 5 정규형 : 릴레이션이 제 5 정규형을 만족하며, 후보키를 통하지 않은 조인 종속을 제거해야 만족하는 정규형</li>
    	</ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 SQL vs NoSQL</strong></summary>
  <ul>
    <li><strong>SQL</strong>
    	<ul>
        <li>관계형 데이터베이스 (Structured Query Language)</li>
        <li>데이터는 정해진 스키마에 따라 테이블에 저장</li>
        <li>데이터는 관계를 통해 여러 테이블에 분산</li>
        <li>장점
        	<ul>
            <li>명확하게 정의 된 스키마, 데이터 무결성 보장</li>
            <li>관계는 각 데이터를 중복없이 한번만 저장</li>
          </ul>
        </li>
      </ul>
    </li>
    <li><strong>NoSQL</strong>
    	<ul>
        <li>비관계형 데이터베이스</li>
        <li>sql과는 다르게 스키마와 관계가 없음</li>
        <li>어떠한 데이터의 형태도 저장 가능</li>
        <li>장점
        	<ul>
            <li>스키마가 없기때문에, 훨씬 더 유연.  언제든지 저장된 데이터를 조정하고 새로운 "필드"를 추가 할 수 있음.</li>
            <li>데이터는 애플리케이션이 필요로 하는 형식으로 저장.  → 데이터를 읽어오는 속도가 빨라짐</li>
            <li><strong>수직 및 수평 확장</strong>이 가능하므로 데이터베이스가 애플리케이션에서 발생시키는 모든 읽기 / 쓰기 요청을 처리 할 수 있음.</li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
</details>
<details>
<summary><strong>💡 인덱스의 장단점</strong></summary>
  <ul>
    <li>장점: 데이터 탐색의 성능이 향상된다.</li>
    <li>단점: 데이터 삽입/삭제 시 인덱스가 변경되기 때문에 성능이 떨어질 수 있다.</li>
  </ul>
</details>