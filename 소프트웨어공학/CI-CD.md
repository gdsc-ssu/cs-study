# 🏃‍♂️ CI/CD

- CI: Continuous Integration(지속적인 통합)

- CD: Continuous Delivery(지속적인 제공) / Continuous Deployment(지속적인 배포)`

![image](https://www.redhat.com/cms/managed-files/styles/wysiwyg_full_width/s3/ci-cd-flow-desktop_edited.png?itok=k5bkXL-F)

소프트웨어의 개발, 테스트와 배포를 모두 통합함으로써 소프트웨어 버그를 쉽게 찾아낼 수 있으며, **지속적인 자동화**와 **모니터링**을 제공하여 더 빠른 배포 주기를 가질 수 있게 만들어 준다.

## 1️⃣ CI(Continuous Integration)란?

![image](https://www.pagerduty.com/wp-content/uploads/2020/01/continuous-integration-2.png)

지속적으로 **품질 관리(Quality Control)**를 적용하는 프로세스를 실행하는 것을 말한다.

소프트웨어의 질적 향상과 소프트웨어를 배포하는데 걸리는 시간을 줄이는데 초점이 맞추어져 있다.

### ✅ 작업 내용

- 소스코드 변경사항을 공유 브랜치로 다시 병합한다.

- 자동화된 단위와 통합테스트로, 변경사항의 정확한 적용여부 및 기존코드와의 충돌여부 등을 확인한다.

### ✅ 작업 순서

1. 개발자가 소스코드를 `repository`에 `commit`한다.

2. 해당 소스코드를 `CI Server`에서 패치한다.

3. `CI Server`에서 소스코드의 빌드를 수행한다.

4. 시나리오에 기반하여 테스트가 수행된다.

   - 시나리오는, 요구사항에 적합하게 설정된다.

5. 빌드 및 테스트 결과에 따라 설정된 기능 수행한다.

6. 해당 내용을 담당자에게 공지한다.

## 2️⃣ CD(Continuous Delivery, Continuous Deployment)란?

![image](https://www.altexsoft.com/media/2017/08/CD-1024x699.png)

**지속적 배포(Continuous delivery)** 란, 팀이 짧은 주기로 소프트웨어를 개발하는 소프트웨어 공학적 접근의 하나이다.

소프트웨어가 언제든지 신뢰 가능한 수준으로 출시될 수 있도록 보증하며, 변경사항의 배포에 대한 비용, 시간, 위험을 줄일 수 있게 한다.

### ✅ 작업 내용

- 배포할 수 있는 유효한 소스코드를 확보하여, 저장소에 자동으로 배포한다.

- 소스코드 변경사항 병합부터 운영환경에 적합한 빌드 제공에 이르는 모든 단계에 테스트 및 소스코드 배포 자동화가 포함된다.

### ✅ Delivery? Deploy?

결정적으로, 파이프라인의 추가 단계 이후 자동화가 얼마나 많이 이루어지고 있냐에 따라서 나뉘기도 한다.

| 제목       | 내용                                                              |
| ---------- | ----------------------------------------------------------------- |
| Deployment | 릴리즈가 가능하다면 배포까지 자동으로 이루어지는 경우             |
| Delivery   | 릴리즈가 가능하다면 배포 단계에서 수동으로 배포가 이루어지는 경우 |

## 3️⃣ CI/CD 도구

- Jenkins
- Circle CI
- TeamCity
- Bamboo
- GitLab
- Github Actions
- Buildkite
- AWS Code Deploy
- Travis CI

> 이외에도 정말 많은 도구가 존재한다.
