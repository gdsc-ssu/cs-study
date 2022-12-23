# SQL 문법 정리

## ✅ SQL이란?
- Structured Query Language(구조적 질의 언어)
- 관계형 데이터베이스 시스템(RDBMS)에서 자료의 관리 및 처리 목적으로 설계된 언어

## ✅ 데이터베이스 언어 종류
- [데이터베이스 언어 및 개념 자세히 살펴보기](https://github.com/gdsc-ssu/cs-study/blob/main/데이터베이스/DB%20개념%20정리.md)
- ▶️ **DDL(Data Definition Language) : 데이터 정의어**
   - 각 릴레이션의 정의를 위해 사용되는 언어 (`CREATE`, `ALTER`, `DROP`, `RENAME`, `TRUNCATE` ...)

- ▶️ **DML(Data Manipulation Language) : 데이터 조작어**
   - 데이터의 추가/수정/삭제 등 데이터 관리를 위한 언어 (`SELECT`, `INSERT`, `UPDATE`, `DELETE` ...)

- ▶️ **DCL(Data Control Language) : 데이터 제어어**
   - 사용자 관리 및 사용자별 릴레이션 또는 데이터로의 관리 및 접근 권한을 제어하는 언어 (`GRANT`, `REVOKE` ...)
   
- ▶️ **TCL(Transaction Control Language) : 트랜잭션 제어어**
   - 트랜잭션을 제어하는 언어 (`COMMIT`, `ROLLBACK`, `SAVEPOINT` ...)
 
## ✅ SQL 문법 특성
1. **대소문자의 구별 X**
	- 단, 서버 환경 또는 DBMS 종류에 따라 데이터베이스 및 필드명의 대소문자를 구분하는 경우도 존재함
1. **SQL 명령문**은 반드시 세미콜론(`;`)으로 끝낼 것
1. **고유 값**의 경우 따옴표(`' '`)로 감쌀 것
1. SQL에서의 객체 표현은 **백틱**으로 감쌀 것
   - ex) ``SELECT `COST`, `TYPE` FROM `INVOICE`;``
1. 한 줄 주석은 문장 앞 `--`를 붙여 사용
1. 여러 줄 주석은 `/* */`을 붙여 사용
   - ex) `/* SELECT * FROM EMP WHERE EMPID=(SELECT * FROM WHERE NAME="GDSC"); */`

## ✅ SQL 문법
### ▶️ CREATE
- **`CREATE DATABASE` : 새로운 데이터베이스 생성**
 ```sql
 CREATE DATABASE 데이터베이스이름;
 ```
 
 - **USE : 데이터베이스 선택**
    - 데이터베이스 생성 후 데이터베이스 사용을 위해 데이터베이스를 선택하는 명령어
 ```sql
 USE 데이터베이스이름;
 ```
 
 - **`CREATE TABLE` : 새로운 테이블 생성**
    - 데이터베이스는 하나 이상의 테이블로 구성
    - 테이블에 데이터를 저장해 관리
    - 테이블 생성 필요 요소 : `테이블 이름`, `필드 목록`, `필드 타입`
    - 필드 타입 : 해당 필드에 저장될 데이터가 가질 수 있는 타입
 
 ```sql
  CREATE TABLE 테이블이름
  (
    필드이름1 필드타입1,
    필드이름2 필드타입2,
    ...
 );
 ```

### ▶️ ALTER
- **`ALTER DATABASE` : 데이터베이스 수정**
   - 데이터베이스의 전체적인 특성 수정
   - 데이터베이스의 특성 : `DATABASE` Dir → `db.opt` 파일에서 확인
   - 데이터베이스의 문자 집합 및 콜레이션 변경 가능
 ```sql
 ALTER DATABASE 데이터베이스이름 CHARACTER SET=문자집합이름;
 ALTER DATABASE 데이터베이스이름 COLLATE=콜레이션이름;
 ```
  - 콜레이션(collation) : 데이터베이스에서 검색 및 정렬과 같은 작업 수행 시 비교를 위한 규칙의 집합
  - ex)``
  ALTER DATABASE Hotel CHARACTER SET=euckr_bin COLLATE=euckr_korean_ci;``

- **`ALTER TABLE` : 테이블 수정**
   - `ADD`를 함께 사용할 경우 테이블에 **필드 추가** 가능
  ```sql
   ALTER TABLE 테이블이름 ADD 필드이름 필드타입
  ```
  
   - `DROP`을 함께 사용할 경우 테이블의 **필드 삭제** 가능
  ```sql
   ALTER TABLE 테이블이름 DROP 필드이름;
  ```
  
  - `MODIFY COLUMN`을 함께 사용할 경우 테이블의 **필드 타입 변경** 가능
  ```sql
   ALTER TABLE 테이블이름 MODIFY COLUMN 필드이름 필드타입;
  ```
  
### ▶️ DROP
- **`DROP DATABASE` : 데이터베이스 삭제**
  ```sql
   DROP DATABASE 데이터베이스이름;
  ```
- **`DROP TABLE` : 테이블 삭제**
  ```sql
   DROP TABLE 테이블이름;
  ```
- **`TRUNCATE TABLE` : 테이블 자체 X, 테이블의 데이터만 삭제**
   - 테이블 자체는 그대로 남게 됨
   - 해당 테이블의 저장된 데이터만 삭제
   - `SELECT`로 테이블의 데이터를 불러올 경우 아무런 데이터도 저장되어 있지 않기에 조회되는 데이터가 없음
  ```sql
   TRUNCATE TABLE 테이블이름;
  ```

### ▶️ INSERT
- **`INSERT INTO` : 테이블에 새로운 레코드 추가**
   - `VALUES` : values 절을 사용해 해당 테이블에 새로운 레코드 추가 가능
 ```sql
 INSERT INTO 테이블이름(필드이름1, 필드이름2, 필드이름3, ...) 
   VALUES (데이터값1, 데이터값2, 데이터값3, ...);
  INSERT INTO 테이블이름 VALUES (데이터값1, 데이터값2, 데이터값3, ...);
 ```
   - 두번째 예시와 같이 필드 이름 생략 가능 → 데이터베이스 스키마와 같은 순서로 필드의 값이 자동 대입됨
      - 생략 가능한 필드 목록
      1. `NULL`을 저장할 수 있도록 설정된 필드
      1. `DEFAULT` 제약 조건이 설정된 필드
      1. `AUTO_INCREMENT` 키워드가 설정된 필드
      
### ▶️ UPDATE
- **`UPDATE` : 레코드의 내용 수정**
   - `UPDATE`문 : 해당 테이블 중 `WHERE` 절의 조건을 만족하는 레코드의 값만 수정
 ```sql
 UPDATE 테이블이름
  SET 필드이름1=데이터값1, 필드이름2=데이터값2, ...
  WHERE 필드이름=데이터값;
 ```
 
### ▶️ DELETE
- **`DELETE` : 레코드 삭제**
   - `DELETE`문 : 해당 테이블의 `WHERE`절 조건을 만족하는 레코드만 삭제
      - 테이블에서 명시된 필드, 그 값이 일치하는 레코드에 삭제 명령 적용
      - `WHERE`절 생략 시 해당 테이블에 저장된 모든 데이터 삭제
 ```sql
 DELETE FROM 테이블이름
  WHERE 필드이름=데이터값;
 ```
 
### ▶️ SELECT
- **`SELECT` : 테이블의 레코드 선택**
   - `FROM` : 레코드를 선택할 테이블의 이름 명시
   - 테이블에서 선택하고자 하는 필드의 이름 `SELECT` 키워드 바로 뒤에 명시
   - `WHERE`절 : 선택할 레코드의 조건 상세 설정 가능
   <br />
   - `SELECT` 문법
 ```sql
 SELECT 필드이름 FROM 테이블이름
  [WHERE 조건]
 ```
  - 모든 필드 선택
 ```sql
 SELECT * FROM GDSC;
 ```
 
  - 특정 조건의 레코드 선택
     - Name의 필드 값이 'GDSC SSU'인 것 만 선택
 ```sql
 SELECT *
  FROM GDSC
  WHERE Name = 'GDSC SSU';
 ```
  
  - 특정 필드만 선택
    - 해당 테이블의 특정 필드만 불러올 수 있음
    - 콜론(`,`)으로 여러개의 필드 이름을 한 번에 명시 가능
 ```sql
 SELECT Name, StudentNum FROM GDSC;
 ```
 
  - `WHERE`절 추가로 특정 조건 만족하는 레코드만 선택 가능

 ```sql
 SELECT Name, StudentNum
  FROM GDSC
  WHERE ID <= 3 AND StudentNum > '20100000';
 ```
 
  - `ORDER BY` 절의 추가로 레코드 정렬 가능
 ```sql
 SELECT * 
  FROM GDSC
  ORDER BY StudentNum;
 ```
  - 별칭(alias)을 이용한 처리
 ```sql
 1. SELECT 필드이름 AS 별칭 FROM 테이블이름;
 2. SELECT 필드이름 FROM 테이블이름 AS 별칭;
 ```
  
## 📌 참고 자료
- [문법 특성 참고 자료](https://edu.goorm.io/learn/lecture/15413/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-sql/lesson/767683/sql%EC%9D%B4%EB%9E%80)
- [문법 참고 자료](http://www.tcpschool.com/mysql/mysql_basic_syntax)
