# 도커를 이용한 컨테이너 관리

# 도커 이미지와 컨테이너

### Image

이미지는 컨테이너를 생성할 때 필요한 요소로 컨테이너의 목적에 맞는 바이너리와 의존성이 설치되어 있습니다. 여러 개의 계층으로 도니 바이너리 파일로 존재합니다

### Container

호스트와 다른 컨테이너로부터 격리된 시스템 자원과 네트워크를 사용하는 프로세스 이미지는 읽기 전용으로 사용하여 변경사항은 컨테이너 계층에 저장됩니다. 

→ 컨테이너에서 무엇을 하든 이미지는 영향을 받지 않습니다

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled.png)

### 도커 이미지 이름 구성

저장소 이름 (Repository Name)

이미지 이름 (Image Name)

이미지 태그 (Image Tag)

도커 이미지 Pull/Push 시에 저장소 이름은 생략하면 기본 저장소인 도커 허브로 인식하고 도커 이미지 태그를 생략하면 최신 리비전을 가리키는 latest로 인식합니다

### 이미지 저장소 (Image Repository)

도커 이미지를 관리하고 공유하기 위한 서버 어플리케이션

---

# 도커를 이용한 컨테이너 관리

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%201.png)

### 컨테이너 시작

도커 create/run 명령어 모두 이미지 없을 경우 자동으로 pull을 먼저 수행하여 이미지를 다운로드 받습니다.

**컨테이너 생성 및 시작**

docker run image

**컨테이너 생성**

docker create [image]

**컨테이너 시작** 

docker start [container]

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%202.png)

docker ps : 실행중인 컨테이너 목록을 확

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%203.png)

docker run nginx

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%204.png)

나가고싶으면 ctl+c

docker create nginx

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%205.png)

docker ps -a

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%206.png)

컨테이너를 지정할 때 container ID를 이용하는 방법과  name을 이용하는 방법이 있습니다.

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%207.png)

### 컨테이너 시작 주요 옵션

- -i : 호스트의 표준 입력을 컨테이너와 연결 (interactive)
- -t : TTY 할당
- - - rm : 컨테이너 실행 종료 후 자동 삭제
- -d : 백그라운드 모드로 실행 (detached)
- - - name : 컨테이너 이름 지정
- -p : 호스트 - 컨테이너 간 포트 바인딩
- -v : 호스트 - 컨테이너 간 볼륨 바인딩

docker run ubuntu:focal

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%208.png)

ubuntu:focal 이미지는 기본 명령어로 bash를 사용하는데 포그라운드 형태로 동작하지 않고 표준 입력을 필요로 하기 때문 -i -t를 사용해야한다.

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%209.png)

그럼 이렇게 잘 붙어있는게 확인이 됩니다.

나가고 싶으면 exit를 치면 됩니다. 그럼 종료가 되는데 만약 나가고 싶지만 계속 실행중으로 두고 싶으면 ctrl+p+q를 해주시면 됩니다.

docker run -d nginx 

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2010.png)

백그라운드 형태로 정상 실행되고 있음을 확인할 수 있습니다.

이번엔 이름을 만들어볼건데요 arsenal이라는 이름을 만들어보겠습니다.

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2011.png)

docker run -p 80:80 -d --name hong nginx

호스트의 80번 포트와 컨테이너의 80번 포트를 연결해보겠습니다.

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2012.png)

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2013.png)

nginx 가 정상적으로 실행되고 있음을 확인할 수 있습니다.

docker pause id

docker unpause id

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2014.png)

### 컨테이너 종료

docker stop [container]  : 컨테이너 종료

docker kill [container] : 컨테이너 강제 종료 

docker stop $(docker ps -a -q) : 모든 컨테이너 종료

### 컨테이너 삭제

docker rm : 컨테이너 삭제

docker rm -f : 컨테이너 강제 종료 후 삭제 

docker run —rm : 컨테이너 실행 종료 후 자동 삭제

docker container prune : 중지된 모든 컨테이너 삭

---

# 엔트리포인트와 커맨드

**Entrypoint**

도커 컨테이너가 실행될 때 고정적으로 실행되는 스크립트 혹은 명령어 생략할 수 있으며, 생략된 경우 커맨드에 지정된 명령어로 수행

**Command**

도커 컨테이너가 실행 할 때 수행할 명령어 혹은 엔트리포인트에 지정된 명령어에 대한 인자 값

docker run ubuntu:focal 

docker run —entrypoint sh ubuntu:focal

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2015.png)

docker run —entrypoint ehco ubuntu:focal ARSENAL

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2016.png)

---

# 환경변수

docker run -i -t -e MY_HOST=[ARSENAL.com](http://arsenal.com/) ubuntu:focal bash

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2017.png)

---

# Docker exec

실행중인 컨테이너에 명령어를 실행

docker exec [container] [command]

docker exec -i -t my-nginx bash : my-nginx 컨테이너에 Bash 셸로 접속하기

docker exec my-nginx env : my-nginx 컨테이너 환경변수 확인하

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2018.png)

---

# 네트워크

veth : virtual eth

docker0 : 도커 엔진에 의해 기본 생성되는 브릿지 네트워크

→ veth eth간 다리 역할

docker run -d -p 80:80 nginx

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2019.png)

docker run -d -p 80 nginx

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2020.png)

## Expose vs Publish

expose 옵션은 그저 문서화 용도

publish 옵션은 실제 포트를 바인

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2021.png)

---

# Docker Volume

### Host Volume

호스트의 디렉토리를 컨테이너 특정 경로에 마운트합니다.

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2022.png)

실행시켜주고 curl  localhost를 살펴보면 hello fastcampus라고 적혀있는 것을 확인할 수 있습니다.

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2023.png)

### 볼륨 컨테이너

특정 컨테이너의 볼륨 마운트를 공유할 수 있다.

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2024.png)

### 도커 볼륨

도커가 제공하는 볼륨 관리 기능을 활용하여 데이터를 보존

기본적으로 /var/lib/docker/volumes/${volume-name}/_data에 데이터가 저장됩니다.

---

# Docker log

호스트 운영체제의 로그 저장 경

---

# 도커 이미지 다루기 : 이미지 빌드

### 도커 이미지 구조

docker run -it —name my_ubuntu ubunut:focal

cat > my_file

(내용 입력)

ctrl+p+q로 빠져나간다

docker ps 를 쳤을 경우 우리가 만든 ubuntu가 실행중이다

docker commit -a hong -m “arsenal fighting” my_ubuntu my-ubuntu:v1 

docker images 를 확인해보면 my-ubuntu:v1 이 생긴다

### docker file로 이미지 생성하기

dockerfile을 기반으로 새 이미지를 생성할 수 있습니다.

**Docker file 문법**

<aside>
💡 FROM : 베이스 이미지 사

RUN
WORKDIR

RUN

CMD

</aside>

docker build -t my-app:v1 ./

![Untitled](%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A5%20%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%20c17737eaaaec482c8bac929a99bbfbe5/Untitled%2025.png)

### 빌드 컨텍스트

도커 빌드 명령 수행 시 현재 디렉토리(Current Working Directory)를 빌드 컨텍스트(Build Context)라고 합니다.
Dockerfile로부터 이미지 빌드에 필요한 정보를 도커 데몬에게 전달하기 위한 목적입니다.

---

# 도커 컴포즈 : 명시적으로 여러 컨테이너 관리하기

도커 컴포즈 ( Docker Compose)

단일 서버에서 여러 컨테이너를 프로젝트 단위로 묶어서 관리
docker-compose.yml YAML 파일을 통해 명시적 관리

프로젝트 단위로 도커 네트워크와 볼륨 관리
프로젝트 내 서비스 간 의존성 정의 가능
프로젝트 내 서비스 디스커버리 자동화
손 쉬운 컨테이너 수평 확장

**프로젝트 (Project)**

도커 컴포즈에서 다루는 워크스페이스 단위.
함께 관리하는 서비스 컨테이너의 묶음.
프로젝트 단위로 기본 도커 네트워크가 생성 됨.

**서비스 (Service)**

도커 컴포즈에서 컨테이너를 관리하기 위한 단위.
scale을 통해 서비스 컨테이너의 수 확장 가능.

**컨테이너 (Container)**

서비스를 통해 컨테이너 관리.