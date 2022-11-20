# Dijkstra algorithm

<br/>

## 📌 다익스트라 알고리즘



- 하나의 특정 마디에서 다른 모든 마디로 가는 최단 경로를 구해주는 알고리즘!
- DP알고리즘에 속하는 알고리즘
    - 최종 최단 거리는 여러개의 최단 거리로 이루어져 있기 때문! (작은 문제가 큰 문제의 부분 집합에 속해있음)

<br/>

## 📌다익스트라 VS 플로이드-워셜


**플로이드-워셜 알고리즘**

- 모든 정점에서 다른 모든 정점으로의 최단 경로를 구해줌

<aside>
  
>💡 ‘거쳐가는 정점’을 기준으로 최단 거리를 구해보자!

</aside>
<br/>

**다익스트라 알고리즘(Dijkstra)**

- 하나의 정점에서 부터 다른 모든 정점으로의 최단 경로를 구해줌

<aside>
  
>💡 가장 적은 비용을 하나씩 선택하자!

</aside>

![https://k.kakaocdn.net/dn/mUTHI/btqZkq0vzfU/kMTM4smM75w7a9qHqFEllk/img.png](https://k.kakaocdn.net/dn/mUTHI/btqZkq0vzfU/kMTM4smM75w7a9qHqFEllk/img.png)

<br/>

## 🚗동작 과정


1. 출발지를 설정
2. ‘최단 거리 테이블’ 초기화
3. 출발 노드를 기준으로 각 노드의 최소 비용을 저장
4. 방문하지 않은 곳 중 거리가 가장 짧은 노드를 선택 (선택한 노드는 방문 처리)
5. 선택한 노드를 거쳐 다른 노드로 넘어가는 경우를 고려하여 최단 거리 테이블을 갱신해줌
6. (4)-(5)의 과정을 반복

<br/>

## 🚘동작 예제



- 1~**2번 과정**

시작 노드를 빨간색인 1번 노드라고 가정

자기 자신까지의 거리는 0으로, 나머지 값은 무한으로 초기화하기!

![https://blog.kakaocdn.net/dn/rrWny/btrfBshmxqX/wMeN4ISRkc7gWxPM2mcxK1/img.png](https://blog.kakaocdn.net/dn/rrWny/btrfBshmxqX/wMeN4ISRkc7gWxPM2mcxK1/img.png)

- **3번 과정**

1번 노드로부터 도달할 수 있는 인접 노드들의 거리를 표에 갱신시켜줌

![https://blog.kakaocdn.net/dn/bysx8O/btrftofXLDl/vJLp0dOk2U8A1YE9SuQ9x1/img.png](https://blog.kakaocdn.net/dn/bysx8O/btrftofXLDl/vJLp0dOk2U8A1YE9SuQ9x1/img.png)

- **4~5번 과정**

1번 노드를 방문 처리하고, 시작 노드인 1번 노드와 가장 가까운 4번 노드를 다음에 탐색할 노드로 선택

선택한 노드를 거쳐 다른 노드로 넘어가는 경우를 고려하여 최단 거리 테이블을 갱신해준다!

- 1→3의 가중치, 1→4→3의 가중치 중 작은걸 택해서 최단 거리 테이블 갱신
- 1→5의 가중치, 1→4→5의 가중치 중 작은걸 택해서 최단 거리 테이블 갱신

![https://blog.kakaocdn.net/dn/c7jlZz/btrfFEVRizL/OIDKfob2QMrMnVcOb6nBTk/img.png](https://blog.kakaocdn.net/dn/c7jlZz/btrfFEVRizL/OIDKfob2QMrMnVcOb6nBTk/img.png)

**해당 과정을 반복해준다**

### 📝코드 전문(Pseudo)

---

최단 경로를 구하려고 하는 마디만 포함하도록 집합 Y를 초기화함.

- F : 이음선의 집합
- touch[i] : Y에 속한 마디들만 중간에 거치도록 하여, 시작점에서 정점 i 로 가는 현재 최단 경로 상의 마지막 이음선을 <v , vi >라고 할 때, Y에 속한 마디 v의 인덱스
- length[i] = Y에 속한 마디들만 중간에 거치도록 하여 시작점에서 정점 i 로 가는 현재 최단경로의 길이

```java
void dijkstra(int n, const number W[][], set_of_edges& F)
{
	index i, vnear;
	edge e;
	index touch[2...n];
	number length[2...n];

	F = null;
	for(i=2;i<=n;i++){ //각 마디에 대해서,
		touch[i] = 1; //v1에서 출발하는 현재 최단경로의 마지막 마디를 v1으로 초기화한다
		length[i] = W[1][i]; 
	}

	repeat (n-1번){
		min = INF;
		for(i=2;i<=n;i++){
			if(0<=length[i]<min){
				min = length[i];
				vnear = i;
			}
		e = touch[vnear]가 인덱스인 마디에서 vnear가 인덱스인 마디로 가는 이음선;
		e를 F에 추가;
		for(i=2;i<=n;i++){
				if(length[vnear] + W[vnear][i] < length[i]){
					length[i] = length[vnear] + W[vnear][i];
					touch[i] = vnear;
				}
		length[vnear] = -1;
			}
		}
	}
}
```

---

### 참고 자료

[https://m.blog.naver.com/ndb796/221234424646](https://m.blog.naver.com/ndb796/221234424646)
