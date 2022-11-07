
  

## 📌플로이드-워셜 알고리즘

- 모든 최단 경로를 구하는 알고리즘
- DP알고리즘에 속하는 알고리즘
    - 노드의 개수가 N 개라고 할 때, N 번 만큼 단계를 반복하며 점화식에 맞게 2차원 리스트를 갱신하기 때문에!   
       
<br/>

## 📌플로이드-워셜 VS 다익스트라


**다익스트라 알고리즘(Dijkstra)**

- 하나의 정점에서 부터 다른 모든 정점으로의 최단 경로를 구해줌

<aside>

>💡 가장 적은 비용을 하나씩 선택하자!
    
  <br/>

</aside>

**플로이드-워셜 알고리즘**

- 모든 정점에서 다른 모든 정점으로의 최단 경로를 구해줌

<aside>

>💡 ‘거쳐가는 정점’을 기준으로 최단 거리를 구해보자!

</aside>
<br/>
<br/>

![https://k.kakaocdn.net/dn/mUTHI/btqZkq0vzfU/kMTM4smM75w7a9qHqFEllk/img.png](https://k.kakaocdn.net/dn/mUTHI/btqZkq0vzfU/kMTM4smM75w7a9qHqFEllk/img.png)

[https://loosie.tistory.com/146](https://loosie.tistory.com/146) 사진 출처!
<br/>
<br/>

## 🚗동작 과정



- 모든 노드 간의 최단거리를 구해야 하므로 **2차원 인접 행렬** 구성
- 라운드마다 각 경로에서 **새로운 중간 노드로 사용할 수 있는 노드를 선택**하고, 더 짧은 길이를 선택하여 줄이는 과정 반복

<aside>

>💡 Floyd-Warshall 알고리즘의 점화식
>
> **$$
>D^{k}[i][j]=minimum(D^{(k-1)}[i][j],D^{(k-1)}[i][k]+D^{(k-1)}[k][j])
>$$**
>
> → **‘i에서 j로 가는 최소 비용’** 과 **‘i에서 k를 거쳐 j로 가는 비용’** 을 비교하여, 더 작은 값으로 갱신

</aside>
<br/>

## 🚘동작 예제


**‘연결되지 않은 간선’** 은 임의의 큰 값(무한)을, **‘자기 자신’** 으로 가는 비용은 0 값을 넣어줌



![https://k.kakaocdn.net/dn/bBc94M/btrGB41I9Us/jTMIsW3SkFjesbIYEMkxj1/img.png](https://k.kakaocdn.net/dn/bBc94M/btrGB41I9Us/jTMIsW3SkFjesbIYEMkxj1/img.png)

**k번 노드를 경유지로** 삼은 후, 최단 거리 테이블 갱신해줌

---

![https://k.kakaocdn.net/dn/bN72MI/btrGB5ffoJb/A7Aml9jUMqrFXZAfbBndTK/img.png](https://k.kakaocdn.net/dn/bN72MI/btrGB5ffoJb/A7Aml9jUMqrFXZAfbBndTK/img.png)

![https://k.kakaocdn.net/dn/cmGAm0/btrGARBMjIQ/L07rPYtomu0KmdMXrsJck0/img.png](https://k.kakaocdn.net/dn/cmGAm0/btrGARBMjIQ/L07rPYtomu0KmdMXrsJck0/img.png)

![https://k.kakaocdn.net/dn/0n5w6/btrGzv0ymiU/CaJkktyzDjVGkfA9mWl8Uk/img.png](https://k.kakaocdn.net/dn/0n5w6/btrGzv0ymiU/CaJkktyzDjVGkfA9mWl8Uk/img.png)

![https://k.kakaocdn.net/dn/7RV1f/btrGzdy4hY9/DnjFxkfvs37noZewWFZbi0/img.png](https://k.kakaocdn.net/dn/7RV1f/btrGzdy4hY9/DnjFxkfvs37noZewWFZbi0/img.png)

<br/>

### 📝코드 전문(Pseudo)

  
  #

- W[i][j]: 정점 i에서 j로 가는 이음선의 가중치
- D[i][j]: 정점 i에서 j로 가는 최단경로
- k: 경유지

```java
void floyd(int n, const number W[][], number D[][])
{
	index i,j,k;
	D = W
	for(k = 1;k <= n;k++)
		for(i = 1;i <= n;i++)
			for(j = 1;j <= n;j++)
				D[i][j] = minimum(D[i][j],D[i][k]+D[k][j]);
}
```
