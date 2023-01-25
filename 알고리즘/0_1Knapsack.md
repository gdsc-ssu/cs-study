# 0-1 Knapsack Problem

## 📌 배낭 채우기

- 도둑 하나가 보석상에 침입했다고 하자. 훔친 물건들의 총 무게가 **배낭의 용량 W**를 초과하면 배낭이 찢어짐

</br>

- 도둑은 **W를 넘지 않으면서** 챙긴 물건들의 **총 값어치가 최대가 되도록** 배낭에 물건을 담고싶어 할 것임

</br>

- 이에 대한 알고리즘이 0-1 Knapsack Problem!

</br>

- **상태 공간 트리**를 구축하여 **BackTracking** 방식으로 해당 문제를 살펴볼 것임

</br>

## 🚗 알고리즘 설계 전략

</br>

- totweight: 지금까지의 무게 합 + 앞으로 넣을 수 있는 무게합
- bound: 지금까지 profit합 + 앞으로 더해질 profit + partial profit

---

1. bound와 totweight를 profit(물건의 값어치)과 weight(물건의 무게)로 초기화
2. 탐욕적으로 아이템을 취함
3. 과정 1,2를 totweight가 W를 초과하게 되는 아이템을 잡을 때까지 반복
4. 남은 공간이 허용하는 무게만큼 마지막 아이템의 일부분을 취하고, 그 일부분에 해당하는 profit을 bound에 더함
5. 마디가 수준 i 에 있다고 하고, 수준 k 에 있는 마디에서 총 무게가 W를 넘는다고 할 때,
    
    <aside>
  
    > $totweight = weight + \displaystyle\sum_{j=i+1}^{k-1}{w_j}$
    >
    > $bound = (profit + \displaystyle\sum_{j=i+1}^{k-1}{p_j})+(W-totweigth)* {p_k \over w_k}$
    >
    > $maxprofit$: 지금까지 찾은 최선의 해답이 주는 값어치
    
    </aside>
    

1. bound ≤ maxprofit 일때, 해당 노드는 유망하지 않다고 결정

---

정리하자면,

- 깊이 우선순위로 각 마디를 방문하여 다음을 수행하면 됨
    - 그 마디의 profit과 weight를 계산
    - 그 마디의 bound를 계산
    - weight<W이고, bound>maxprofit이면 검색을 계속
    - 그렇지 않다면, 되추적함

</br>

## 🚘동작 예제

![n은 물건의 개수](https://blog.kakaocdn.net/dn/pdZVJ/btqNllWGj6z/Wu7rgfv8iCFxW1lOkiYWOk/img.png)

n은 물건의 개수


---

**각 마디 별로 계산 실행!**

---

1. ***maxprofit = 0 으로 설정***

</br>

2. ***마디 (0,0)을 방문***
    1. **그 값어치 및 무게 계산**
        1. profit = 0
        2. weight = 0
    2. **totweight와 bound 계산**
        1. 2 + 5 + 10 > W이므로 3번째 아이템을 취하면 무게 합이 W를 넘음
        2. k = 3이므로 bound, totweight 공식에 의해 
        3. totweight = weight + 0 + 2 + 5 = 7
        4. bound = profit + 40 + 30 + (16 - 7) x 50/10 = 115
    3. **0(무게 값) < W 이고 115(bound) > 0(maxprofit)** 이므로 이 마디는 유망하다고 결정

</br>

3. ***마디 (1,1)을 방문***
    1. **그 값어치 및 무게 계산**
        1. profit = 0 + 40 = 40
        2. weight = 0 + 2 = 2
        3. profit이 40이므로 기존의 maxprofit인 0 보다 큼
        4. maxprofit을 40으로 갱신
    2. **totweight와 bound를 계산**
        1. 2 + 5 + 10 > W이므로 3번째 아이템을 취하면 무게 합이 W를 넘음
        2. k = 3이므로 bound, totweight 공식에 의해
        3. totweight = weight  + 2 + 5 = 7
        4. bound = profit + 30 + (16 - 7) x 50/10 = 115
    3. **2(무게 값) < W 이고 115(bound) > 40(maxprofit)** 이므로 이 마디는 유망하다고 결정

</br>

4. ***마디 (2, 1)을 방문***
    1. **그 값어치 및 무게 계산**
        1. profit = 40 + 30 = 70
        2. weight = 2 + 5 = 7
        3. profit이 70이므로 기존의 maxprofit인 40 보다 큼
        4. maxprofit을 70으로 갱신
    2. **totweight와 bound를 계산**
        1. 2 + 5 + 10 > W이므로 3번째 아이템을 취하면 무게 합이 W를 넘음
        2. k = 3이므로 bound, totweight 공식에 의해
        3. totweight = weight  + 0 = 7
        4. bound = profit + (16 - 7) x 50/10 = 115
    3. **7(무게 값) < W 이고 115(bound) > 70(maxprofit)** 이므로 이 마디는 유망하다고 결정

.

.

.

해당 방법을 반복해주면 됨!

![https://blog.kakaocdn.net/dn/kyQKI/btqNfrq2kSK/KFsto4tfrsFFqRMSS3MuQ1/img.png](https://blog.kakaocdn.net/dn/kyQKI/btqNfrq2kSK/KFsto4tfrsFFqRMSS3MuQ1/img.png)

### 📝코드 전문(Pseudo)

---

```java
void knapsack (index i, int profit, int weight) {
	if (weight <= W && profit > maxprofit) { // 지금까지 최고의 답
		maxprofit = profit;
		numbest = i; 
		bestset = include; 
	}
    
	if (promising(i, profit, weight)) {
		include[i+1] = “YES”; // Include w[i+1]
		knapsack(i+1, profit+p[i+1], weight+w[i+1]);
		include[i+1] = “NO”; // Not include w[i+1]
		knapsack(i+1, profit, weight);
	}
}

bool promising(index i, int profit, int weight) {
	index j, k; 
	int totweight; 
	float bound;
	if (weight >= W) return FALSE;  //자식마디로 확장할 수 있을 때만 유망하다.
	else {							//자식마디에 쓸 공간이 남아 있어야 한다. 
		j = i+1;
	bound = profit; 
	totweight = weight;
	while ((j <= n) && (totweight +w[j] <= W)) {  //가능한 많은 아이템을 취한다. 
		totweight = totweight + w[j]; 
		bound = bound + p[j];
		j++
	}
	k=j;  		
	if (k <= n)  // k째 아이템의 일부분을 취함
		bound = bound +(W–totweight)*p[k]/w[k];
	
    return bound > maxprofit;
}
}
```
