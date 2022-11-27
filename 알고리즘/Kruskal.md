# Kruskal Algorithm

</br>

## 📌 크루스칼 알고리즘

- **최소 신장 트리(MST)** 를 구하는 알고리즘
- Greedy Algorithm

</br>


## 📌최소 신장 트리란?

**신장 트리? Spanning Tree**

- 그래프 내에 있는 모든 정점을 연결하고, 사이클이 없는 그래프

</br>


**최소 신장 트리? Minimum Spanning Tree**

- Spanning Tree 중에서 사용된 간선(edge)들의 가중치 합이 최소인 트리

</br>

  
> 💡 Kruskal algorithm은 그래프의 **모든 정점** 을 **최소 비용** 으로 연결하는 최적 해답을 구하는 것!
  
</br>


## 🚗 동작 과정

1. 그래프의 간선을 가중치 오름차순으로 정렬 </br>

2. 간선을 하나씩 확인하며, 현재의 간선이 사이클을 발생시키는지 확인 </br>

    a. 사이클이 발생하지 않는 경우, 최소 신장 트리에 포함 </br>

    b. 사이클이 발생하는 경우 최소 신장 트리에 포함시키지 않음 </br>

3. 모든 간선에 대하여 2-4의 과정을 반복
4. 선택된 간선의 개수가 정점의 개수 - 1만큼 되면 종료

## 🚘 동작 예제

**[1번 과정]**

    가중치 순으로 오름차순 정렬

![https://i.imgur.com/FZP5haF.png](https://i.imgur.com/FZP5haF.png)

**[2번 과정]**

    [2.a] 

      a-b 간선 선택

![https://i.imgur.com/cygqIT7.png](https://i.imgur.com/cygqIT7.png)

    [2.a] 

        a-d 간선 선택

![https://i.imgur.com/TzWXNYV.png](https://i.imgur.com/TzWXNYV.png)

    [2.b]

        b-d를 선택하면 a-b-d 사이클이 형성되므로 선택하지 않음

![https://i.imgur.com/si8xA9K.png](https://i.imgur.com/si8xA9K.png)

**[4번 과정]**

    b-c 선택 시, 선택된 간선의 개수가 정점의 개수 - 1 이므로 종료

![https://i.imgur.com/PQZwcsT.png](https://i.imgur.com/PQZwcsT.png)

## ♾️ 사이클 판단하기

[2.b] 과정에서 사이클이 형성되면 넘어갔었는데, 사이클인지 아닌지 어떻게 판단할까?

</br>


> 💡 **Union-Find** 자료구조를 활용!

</br>

Union-Find란?

- **서로소 집합(Disjoint Set)** 을 표현하는 자료구조
- **Union 연산** : 서로 다른 두 집합을 병합
- **Find 연산** : 집합 원소가 어떤 집합에 속해있는지 찾음

</br>

### 📝코드 전문(Pseudo)

- **n**: 입력으로 들어온 값의 정점의 개수
- **m**: edge의 개수
- **initial(n)**: n개의 서로소 부분집합을 초기화
- **p = find(i)** : 인덱스 i가 포함된 집합의 포인터 p를 넘겨줌
- **merge(p,q)**: 두개의 집합을 가리키는 p와 q를 병합
- **equal(p,q)**: p와 q가 같은 집합을 가리키면 true를 넘겨줌

```
void kruskal(int n, int m, set_of_edges E, set_of_edges& F){
		index i, j
		set_pointer p, q;
		edge e;

		sort(set_of_edges); // edge들을 가중치 오름차순으로 정렬
		initial(n); //n개의 서로소 부분집합을 초기화

		while(number of edges in F is less than n-1){
			// e = 아직 고려되지 않은 가중치 중, 가장 크기가 작은 것
			// i, j = 선택된 edge의 양쪽 정점
			p = find(i);
			q = find(j);

			if(!equal(p,q)){ //정점 i가 속한 집합과 j가 속한 집합이 다르다면
				merge(p,q); //정점 i와 정점 j가 속한 집합을 병합
				add e to F; // 해당 edge를 F에 포함시킴
			}
		}
	}
```
