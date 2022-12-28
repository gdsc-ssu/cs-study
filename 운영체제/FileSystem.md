# 🐛💨 파일 시스템(File System)

## 🐸 파일 시스템(File System) 이란?

- 컴퓨터 내부의 (파일과 자료)를 쉽게 발견하고 접근할 수 있도록, 보관 및 조직하는 체계이다.
  - 자료를 클러스터 또는 블록이라고 불리는 일정한 단위에 새겨 넣는다.
    - 파일 하나가 필요로 하는 디스크의 최소 공간
- 크기가 일정한 블록들이 모여있는 배열인 **자료 보관 장치** 로 파일의 물리적 소재를 관리한다.
  - 이 배열의 요소들을 묶고 풀고 조직하면서 파일과 디렉토리를 생성한다.
  - 이 때 배열에 공백을 두어서 이를 구분한다.
  - **자료 보관 장치**
    - 하드 디스크
    - CD-ROM
- 파일을 저장하는 시스템에 따라서 다양하게 존재한다.
  - Windows
    - FAT16
    - FAT32
    - NTFS
  - Linux
    - ext2
    - ext3
    - ext4
  - Mac OS
    - HFS
    - HFS+
  - Google
    - GFS
  - ...

> ✨ 저장 매체의 공간이 증가 할수록 보관하는 파일의 수 또한 점점 증가하게 되어 별도의 관리 시스템이 필요하게 되었다. 그래서 개발된 것이 `파일시스템`!

## 🐸 파일 시스템(File System)의 특징

- 계층적 디렉토리 구조
- **디스크 파티션** 별로 파일시스템을 하나씩 둘 수 있다.
  - 파일시스템에 대한 실제 저장소
- 커널 영역에서 동작
- 많은 정보를 가짐
  - _총 블록수, 블록 위치, 디렉토리 구조, 파일 정보 등 파일의 속성, 파일에 대한 연산 등_

## 🐸 파일 시스템(File System)의 목적

- HDD와 메인 메모리 속도차 줄이기
- 파일 CRUD 기능을 원할히 수행하기
- 파일 관리, 하드디스크 용량의 효율적 이용

## 🐸 파일 시스템(File System)의 역할

- 파일관리 : 파일 저장, 참조, 공유
- 보조 저장소 관리 : 저장 공간 할당
- 파일 무결성 메커니즘 : 파일이 의도한 정보만 포함하고 있음을 의미
- 접근 방법 : 저장된 데이터에 접근할 수 있는 방법 제공

## 🐸 파일 시스템(File System)의 구조

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCOa2C%2Fbtq2gR2iTgy%2FiZak8mRBUVdvDslK0J8cL0%2Fimg.png)

- **메타 영역**
  - 데이터 영역에 기록된 파일의 이름, 위치, 크기, 시간정보, 삭제유무 등 파일의 정보
- **데이터 영역**
  - 파일의 데이터
- 저장된 파일
  - 실제 정보 내용
- 디렉토리
  - 정리, 검색 기능

## 🐸 파일 시스템(File System)의 접근 방법

- 파일에 접근하여 데이터를 읽는 방법

### 🐾 순차 접근

![image](https://velog.velcdn.com/images/gang_shik/post/900e3489-c26f-4d13-a955-f0cad36178c5/image.png)

- 파일의 정보가 레코드 순서대로 차례차례 처리된다.
- I/O 시스템 콜 발생시 포인터를 앞으로 보내면서 읽거나 쓴다.
- 포인터가 뒤로 돌아가면 지정한 offset만큼 되감기를 해야한다.
- **테이프 모델**에 기반을 둔다.

### 🐾 직접 접근

![image](https://velog.velcdn.com/images/gang_shik/post/4d29da24-a761-4e00-a0de-e7bbf8c5d154/image.png)

- 순서 없이 레코드를 빠르게 읽고 쓴다.
  - **디스크 모델** 기반
  - 무작위 파일 블록에 대한 임의 접근를 허용한다.
- 대규모 정보를 즉각적으로 접근하는 데 유용하다.
  - 데이터베이스에 이용한다.
- `직접 접근 파일`을 가지고 `순차 파일 기능`을 쉽게 구현할 수 있다.
  - 현재 위치에 대한 정보를 담고 있는 변수가 유지되어야 한다.

### 🐾 기타 접근

![image](https://velog.velcdn.com/images/gang_shik/post/58ac68d4-4878-4e60-8ea1-60bae1160558/image.png)

- `직접 접근 파일`에 기반하여 색인 구축한다.
- 크기가 큰 파일을 입출력 탐색할 수 있게 도와준다.

## 🐸 디스크 구조

![image](https://velog.velcdn.com/images/gang_shik/post/283b557d-6de0-4ade-ade4-0146ad655533/image.png)

- **파티션(Partition)** 은 연속된 저장 공간을 하나 이상의 연속되고 독립적인 영역으로 나누어서 사용할 수 있도록 정의한 규약이다.

## 🐸 디렉토리 구조

- 파일 이름을 해당 디렉토리 항목으로 변환해주는 심벌 테이블이다.

### 🐾 1단계 디렉터리

![image](https://velog.velcdn.com/images/gang_shik/post/524f5043-bb45-4130-9567-7017ec4b923e/image.png)

- 파일들은 서로 유일한 이름을 가진다.
- 서로 다른 사용자라도 같은 이름 사용 불가능하다.

### 🐾 2단계 디렉토리

![image](https://velog.velcdn.com/images/gang_shik/post/beefdde8-98a6-49a8-951b-7a95113e0c52/image.png)

- 사용자 개별 디렉토리 생성
- UFD(User File Directory)
  - 자신만의 사용자 파일 디렉토리
- MFD(Master File Directory)
  - 사용자의 이름과 계정번호로 색인되어 있는 디렉토리

### 🐾 트리 구조 디렉토리

![image](https://velog.velcdn.com/images/gang_shik/post/6c22bf2f-6e8c-45ca-9e52-828afdb622c8/image.png)

- 2단계 구조 확장된 다단계 트리 구조이다.
- `1bit`를 활용하여, 일반 파일(0)인지 디렉터리 파일(1) 구분한다.

### 🐾 그래프 구조 디렉토리

![image](https://velog.velcdn.com/images/gang_shik/post/11b26e15-fc4c-45bf-8bc5-f8ac0935a57b/image.png)

- 하위 디렉토리가 아닌 파일에 대한 링크만 허용한다.
  - 링크가 있으면 우회하여 순환을 피할 수 있다.
- **가비지 컬렉션**을 이용한다.
  - 전체 파일 시스템을 순회하고 접근 가능한 모든 것을 표시한다.

## 🔍 참고자료

- [파일 시스템(File System)](https://velog.io/@gang_shik/%ED%8C%8C%EC%9D%BC-%EC%8B%9C%EC%8A%A4%ED%85%9CFile-System)
- [[OS] 파일 시스템(File System)이란?](https://security-nanglam.tistory.com/228)
- [CS-Free-study/CS-Study - FileSystem.md](https://github.com/CS-Free-study/CS-Study/blob/main/contents/operating-system/FileSystem.md)
