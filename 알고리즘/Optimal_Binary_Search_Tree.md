# **Optimal Binary Search Tree**

## 📌 최적 이진 탐색 트리

- **가능한 이진 검색 트리 중 key를 찾는데에 걸리는 평균 시간이 가장 짧은 이진 검색 트리**
    - **이진 탐색 트리(Binary Search Tree)** 란?
        - 이진 트리를 검색 목적으로 사용하는 것
        - 각 노드는 하나의 유일한 키를 가지고 있음
        - 왼쪽에는 같거나 더 작은 값을, 오른쪽에는 더 큰 값을 저장함

    - 평균 탐색 시간은?
        - 한 노드에 담긴 $key_m$ 이 찾고자하는 search key일 확률:  $p_m$
        - $key_m$ 을 찾기까지의 비교횟수: $c_m$ 라 할때,
        - $p_m$과 $c_m$의 곱의 합

        </br>
        
        > $\displaystyle\sum_{m=i}^{j}{c_mp_m}$
        
</br>

## 🚗 알고리즘 설계 전략

![https://blog.kakaocdn.net/dn/bvJ6lF/btqR6voM2X8/U6BrCfIgY6UuQxSG9fu2hk/img.png](https://blog.kakaocdn.net/dn/bvJ6lF/btqR6voM2X8/U6BrCfIgY6UuQxSG9fu2hk/img.png)

- root를 추가할 때 마다 기존의 트리는 그 root의 subtree가 되므로 비교횟수가 각각 한번씩( $c_i(=1)*p_i$) 더 늘어남

</br>

- 따라서 $A[1][n] = A[1][k-1]+p_1+...+p_{k-1}+p_k+A[k+1][1]+p_{k+1}+...+p_n$
    - A는 최적의 평균 탐색 시간 값을 담은 배열
    - $A[i][j] = key_i$ 부터 $key_j$ 까지의 최적 평균 탐색시간

</br>

- 결론적으로 아래와 같은 재귀 관계식이 도출됨

<aside>
  
  > $A[1][n]=minimum_{1\leq k \leq n}(A[1][k-1]+A[k+1][n])+ \displaystyle\sum_{m=1}^{n}{p_m}(i\lt j)$
                                                                                                   
</aside>

</br>

- 왼쪽 sub tree의 노드 개수가 0개일 때부터 n-1개일 때까지를 앞의 것의 결과를 토대로 순서대로 구함(bottom-up 방식)

![https://blog.kakaocdn.net/dn/cgOcOO/btqSmBHBmo0/F32fxRKq90C2Rblal5qof1/img.png](https://blog.kakaocdn.net/dn/cgOcOO/btqSmBHBmo0/F32fxRKq90C2Rblal5qof1/img.png)

- 시간 복잡도: $Θ(n^3)$

## 🚘동작 예제

![https://blog.kakaocdn.net/dn/vh9Vx/btqSduWQRBS/Z6YkgKPC9WmIM5T2qfqFrK/img.png](https://blog.kakaocdn.net/dn/vh9Vx/btqSduWQRBS/Z6YkgKPC9WmIM5T2qfqFrK/img.png)

</br>

### 📝코드 전문(Pseudo)

---

```java
void optsearchtree(int n, const float p[], float& minavg, index R[][]) {
  index i, j, k, diagonal;
  float A[1..n+1][0..n];
  
  for(i=1; i<=n; i++) {
    A[i][i-1] = 0;
    A[i][i] = p[i];
    R[i][i-1] = 0;
  }
  
  A[n+1][n] = 0;
  R[n+1][n] = 0;
  
  for(diagonal = 1; diagonal <= n-1; diagonal++)
    for(i=1; i <= n-diagonal; i++) {
      j = i + diagonal;
      A[i][j] = minimum(A[i][k-1]+A[k+1][j])) + sum of pi ~ pj; //basic operation
      R[i][j] = a value of k that gave the minimum;
    }
    minavg = A[1][n];
}

//배열 R을 이용해 트리 생성
nodepointer tree(index i, j) {
  index k;
  node_pointer p;
  k = R[i][j];
  if(k==0)
    return NULL;
  else {
    p = new nodetype;
    p->key = key[k];
    p->left = tree(i,k-1);
    p->right = tree(k+1,j);
    return p;
  }
}
```
