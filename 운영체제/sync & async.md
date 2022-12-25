# 동기와 비동기
> 다음 작업이 요청되는 시간과 관련된 개념

## 사전 지식
- **Sync VS Async**
   - 호출되는 함수의 작업 완료 여부를 어디서 신경쓰는가?
   - 처리해야 하는 작업들을 **어떤 흐름**으로 처리할 것인가?
   
- **Blocking VS Non-Blocking** 
   - 호출되는 함수가 바로 리턴
   - 처리되어야 하는 하나의 작업이 **전체적인 작업 흐름에 영향**을 미치는가?

## 동기(Synchronous)와 비동기(Asynchronous)란?
### ▶️ 동기(Synchronous)
- 현재 작업의 응답이 끝남과 동시에 다음 작업이 요청된다.
   - `Request` 이후 `Response`를 받아야 다음 동작이 이루어진다.
- 함수 호출부에서 호출되는 함수가 결과를 반환할 때까지 기다린다.
   - 특정 작업을 처리할 동안 다른 작업은 정지 상태를 유지한다.
   - 실제 CPU가 느려지는 것은 아니다. (이 때, 시스템 효율은 저하될 수 있다.)
- 작업 완료 여부를 계속 추적해 확인한다.
- 직관적이고 간단한 설계
- 결과가 주어질 때까지 다른 작업 수행 없이 대기
```js
function syncRun(a, b) {
    return a + b
}
const result = syncRun(1, 2);

console.log("시작");
console.log("결과:", result);
console.log("끝");

/**출력 결과
 * 시작
 * 결과: 3
 * 끝
 */
```

### ▶️ 비동기(Asynchronous)
- 현재 작업의 응답이 끝나지 않은 상태에서 다음 작업이 요청된다.
   - `Request` 이후 `Response`를 받지 않아도 다음 동작 이루어진다.
- 함수 호출부에서 반환되는 결과를 기다리지 않으며, 다른 함수(`callback`)에서 결과를 처리한다.
   - 특정 작업 처리할 동안 다른 작업 수행 가능
   - 컴퓨터 자원의 효율적 사용
   - `Request` 시 할 일 끝난 후 **콜백함수**를 통해 처리 결과 전달
      - 콜백 시 호출받은 함수 : 응답(확인) 수행
- 동기(Synchronous)방식에 비해 복잡하고 덜 직관적인 설계
- 작업 완료 여부를 확인하지 않는다.
	- `Request` 결과가 주어지기 전에 다른 작업 가능
    - 자원 사용의 효율성 증대
```js
function asyncRun(a, b) {
    return a + b
}

let result;
setTimeout(() => {
    result = asyncRun(1, 2);
}, 1000);

console.log("시작");
console.log("결과:", result);
console.log("끝");

/**출력 결과
 * 시작
 * 결과: undefined
 * 끝
 */
```
<img width="667" alt="스크린샷 2022-11-19 오전 10 09 04" src="https://user-images.githubusercontent.com/66112716/202826696-59e6180e-cb7b-422e-9251-5c8172bebafa.png">

## Blocking & Non-Blocking
멀티 스레딩, I/O에서 사용되는 개념
**함수의 리턴 시점** & **제어권**에 따른 차이점

### ▶️ Blocking
- **호출된** 함수가 해당 작업이 모두 끝날 때까지 **제어권을 가진다.**
- **호출한** 함수가 **대기**하는 상태
<img width="456" alt="스크린샷 2022-11-19 오후 2 53 01" src="https://user-images.githubusercontent.com/66112716/202836840-1e2cadf4-9d9f-453a-85d9-d9fc9578f266.png">

### ▶️ Non-Blocking
- **호출된** 함수가 **바로 return**해 **호출한** 함수에게 **제어권 부여**
   - 다른 일을 할 수 있다.
- 호출되는 함수의 return 여부에 따라 `Blocking` vs `Non-Blocking` 결정

<img width="455" alt="스크린샷 2022-11-19 오후 2 53 33" src="https://user-images.githubusercontent.com/66112716/202836919-97e91afe-a033-478c-b443-51c104fb3ea1.png">

### ▶️ Blocking vs Non-Blocking
- **Non-Blocking** : 
   1. 호출된 함수가 바로 `return`해서 호출한 함수에게 제어권을 넘겨준다.
   1. 호출한 함수가 다른 일을 할 수 있는 기회를 준다.
- **Blocking** : 
   1. 호출된 함수가 자신의 작업을 모두 마칠 때까지 호출한 함수에게 제어권을 넘겨주지 않고 대기하도록 한다.

## Sync & Async + Blocking & Non-Blocking
|     Sync & Blocking     |     Async & Blocking     |
| :---------------------: | :----------------------: |
|   Sync & Non-blocking   |   Async & Non-blocking   |

### ▶️ Sync & Blocking
- 가장 기본적으로 생각하는 **Sync**
- 함수 호출 시 **호출을 받은 쪽**에서 제어권을 가진다.
- 결과값이 반환될 때까지 다음 동작은 시행되지 않는다.

### ▶️ Async & Blocking
- 작업 완료 여부를 호출된 쪽에서 관여한다.
- 호출된 함수 쪽에서 제어권을 가진다.
- 순서대로 진행되지 않아도 되지만 제어권이 넘어간 상태이다.
- 대기 시간이 발생한다.
- **Sync & Blocking**과 거의 같다.
- 자주 사용되지 않는다.

### ▶️ Sync & Non-blocking
- 함수가 완료되지 않아도 제어권을 넘겨준다.
- 함수 호출부에서 다음 동작 시행이 가능하다.
- 주기적으로 함수의 완료 여부를 확인해야 한다.

### ▶️ Async & Non-blocking
- 가장 기본적으로 생각하는 **Async**
- 함수 호출 시 제어권을 다시 호출한 쪽으로 넘겨준다.
- 호출받은 쪽에서 다음 동작을 이어나가며 작업 완료 시 콜백 함수 결과를 리턴한다.

<img width="678" alt="스크린샷 2022-11-19 오후 4 59 30" src="https://user-images.githubusercontent.com/66112716/202841483-5c2cdac6-5d53-42cd-ace7-c63654da52ce.png">

## 동기==블로킹, 비동기==논블로킹?
- `동기`, `비동기` : **작업 수행의 주체**가 **2개 이상**이어야 한다.
   - 작업의 시간을 맞출 경우 : **동기**
   - 작업의 시간을 맞추지 않을 경우, 서로 관계가 없을 경우 : **비동기**
   
- `블로킹`,`논블로킹` : **작업의 대상**이 **2개 이상**이어야 한다.      
→ 보는 관점이 다르기에 4가지 조합이 가능하다.

## 참고자료
- [개념 참고 자료1](https://cotak.tistory.com/136)
- [개념 참고 자료2](https://github.com/Seogeurim/CS-study/blob/main/contents/operating-system/README.md)
- [개념 참고 자료3](https://velog.io/@soyeon207/%EB%8F%99%EA%B8%B0-%EB%B9%84%EB%8F%99%EA%B8%B0-blocking-non-blocking)