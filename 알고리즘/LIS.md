# LIS(Longest Increasing Subsequence)

**최장 증가 부분 수열**(LIS, Longest Increasing Subsequence)은 배열의 부분 수열 중, **오름차순 조건**을 만족시키는 **길이가 가장 긴** 부분 수열이다.

예를 들어, 배열 `Arr`이 [4, 2, 5, 8, 4, 11, 15]이라면, LIS는 [4, 5, 8, 11, 15] 이 된다.

<br>

## 구하는 방법

배열 `Arr`이 주어졌을 때, **LIS의 길이**를 구하는 방법을 알아보자.

<br>

### 방법1. DP

`dp` 배열의 각 원소는 "해당 위치 이전의 원소들"에 대하여 "해당 위치의 `Arr`의 원소"를 최댓값으로 하는 LIS의 길이이다.

위를 구현하기 위해서는 이중 for문을 사용하면 되며, 
`dp` 배열의 최댓값이 LIS의 길이가 된다.

```js
// get LIS length with DP
const arr = [4, 2, 5, 8, 4, 11, 15];
const dp = Array(arr.length).fill(1);

// 매번 i 위치까지의 LIS 구하기
for (let i = 1; i < arr.length; i++) {
  for (let j = 0; j < i; j++) {
    if (arr[j] < arr[i]) {
      dp[i] = Math.max(dp[i], dp[j] + 1);
    }
  }
}

const answer = Math.max(...dp);
console.log(answer);
```

<br>

하지만 dp를 이용한 방식은 간단하지만 **$O(n^2)$의 시간복잡도**를 갖는 문제가 있다.

<br>

### 2. 이분 탐색

이분 탐색을 사용한 방식은 **$O(nlogn)$의 시간복잡도**를 가져 보다 빠르게 LIS 길이를 찾을 수 있다.

이 방식의 핵심 아이디어는 "**LIS의 마지막 원소가 작을수록 더 긴 LIS를 생성할 수 있다**"이다. 그래서 현재 생성된 LIS가 의 마지막 원소가 새로운 원소보다 작은 경우, 들어갈 위치를 **이분 탐색**을 찾은 후 대체시켜 LIS 길이를 찾아낸다.

```js
// get LIS length with Binary Search
const arr = [4, 2, 5, 8, 4, 11, 15];
const lis = [arr[0]];

for (let i = 1; i < arr.length; i++) {
  // 이분 탐색으로 위치 찾기
  let left = 0;
  let right = lis.length;

  while (left < right) {
    const mid = Math.floor((left + right) / 2);
    if (arr[i] > lis[mid]) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }

  if (right === lis.length) {
    lis.push(arr[i]);
  } else {
    lis[right] = arr[i];
  }
}

console.log(lis.length);
```

<br>

하지만 이 방식은 **단순히 LIS의 길이만 구할 수 있지, 실제 LIS가 반환되진 않는다.**

- 예시) `arr`: [3, 5, 2, 6, 1] → `lis`: [ 1, 5, 6 ]

> 실제 반환되는 LIS를 구하고 싶다면, 각 원소가 들어간 인덱스 정보를 별도로 저장하면 된다.

<br>

## 관련 문제

- 백준) [가장 긴 증가하는 부분 수열](https://www.acmicpc.net/problem/11053)
- 백준) [가장 긴 증가하는 부분 수열 2](https://www.acmicpc.net/problem/12015)
- 백준) [병사 배치하기](https://www.acmicpc.net/problem/18353)

<br>

## 참고 자료

- https://namu.wiki/w/%EC%B5%9C%EC%9E%A5%20%EC%A6%9D%EA%B0%80%20%EB%B6%80%EB%B6%84%20%EC%88%98%EC%97%B4