# **Chain Matrix Multiplication**

## 📌 연쇄 행렬 곱셈

- **행렬을 곱할 때 비용이 가장 적은 순서를 찾아내는 알고리즘**

</br>

- **M1, M2, M3, M4 네개의 행렬**을 곱한다고 한다면,
    1. ((M1 x M2) x M3) x M4
    2. (M1 x M2) x (M3 x M4)
    3. (M1 x (M2 x M3)) x M4
    4. M1 x (M2 x (M3 x M4))
    5. M1 x ((M2 x M3) x M4)

</br>

- 5가지 경우의 수가 생길 것이며, 각 경우의 수에 따라 곱셈 횟수가 달라질 것이므로 이 중, 가장 적은 곱셈 비용을 찾아내기 위한 알고리즘을 **Chain Matrix Multiplication** 이라 함

## 🚗동작 과정

- **M[i][j]** 는 **행렬 Mi부터 Mj 까지의 곱셈 연산 횟수**를 의미

</br>

- d는 dimension을 의미
    - A, B, C, D 행렬이 각각 A = 20 x 1, B = 1 x 30, C = 30 x 10, D = 10 x 10라 할때
    - **d0** = 20, **d1** = 1, **d2** = 30, **d3** = 10, **d4** = 10

<aside>
    
</br>
  
> 💡 Chain Matrix Multiplication 알고리즘의 점화식
>
> $M[i][j]=minimum(M[i][k]+M[k+1][j]+d_{i-1}d_kd_j)\quad(i\leq k \leq j-1)$
>
> $M[i][j]=0 \quad(i==j)$

</aside>

</br>

## 🚘동작 예제

- 위 동작 과정에서의 예시를 활용(A = 20 x 1, B = 1 x 30, C = 30 x 10, D = 10 x 10)

</br>

- 행렬이 N개 일때, **M[1][N]** 의 값을 구하는 것이 최종 목표이고 값을 구하기 위해서는 각 구간의 값을 모두 구해서 최솟값을 찾아야 함

</br>

- M[1][4]의 값을 구하려면?
    - M[1][1] + M[2][4] + d0 x d1 x d4
    - M[1][2] + M[3][4] + d0 x d2 x d4
    - M[1][3] + M[4][4] + d0 x d3 x d4 중 최솟값을 찾아야 함

</br>

- M[i][j]의 값은 대각선을 하나씩 증가시키며 아래와 같이 구할 수 있음.
1. **(i,i 구하기)**

| (0,0) | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| 1 | 0 |  |  |  |
| 2 |  | 0 |  |  |
| 3 |  |  | 0 |  |
| 4 |  |  |  | 0 |

</br>

2. **(1,2) ~ (3,4)**

| (0,0) | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| 1 | 0 | 600 |  |  |
| 2 |  | 0 | 300 |  |
| 3 |  |  | 0 | 3000 |
| 4 |  |  |  | 0 |

</br>

3. **(1,3) ~ (2,4)**

| (0,0) | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| 1 | 0 | 600 | 500 |  |
| 2 |  | 0 | 300 | 400 |
| 3 |  |  | 0 | 3000 |
| 4 |  |  |  | 0 |

</br>

4. **(1,4)**

| (0,0) | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| 1 | 0 | 600 | 500 | 600 |
| 2 |  | 0 | 300 | 400 |
| 3 |  |  | 0 | 3000 |
| 4 |  |  |  | 0 |

---

### 가장 최소의 비용을 가지는 곱셈 순서를 구하고 싶다면?

→ **S[i][j] 배열**을 구하면 됨!

- S[i][j] 배열은 어떻게 구하는가?
    - 점화식에서 k의 값을 저장하면 됨

<aside>
  
> 💡 M[i][j]에서 k값을 무엇으로 잡았을 때 가장 최소가 되었는가? 에 대한 정보를 저장하는 배열

</aside>

### 📝코드 전문(Pseudo)

---

```java
matrix_chain(i, j)
// 행렬 곱셈 A_i ... A_j의 최소 곱셈 횟수를 리턴한다.
{
    for (int i = 1; i <= n; i++)
        m[i, i] = 0;
    
    for (int r = 1; r <= n-1; r++)
        for (int i = 1; i <= n-r; i++){
            j = i+r;
            min = INT_MAX;
            for(int k = i; k <= j-1; k++){
                opt_val = m[i, k] + m[k+1, j] + p_{i-1}*p_{k}*p_{j};
                if(min <= opt_val)
                    min = opt_val;
            }
            m[i, j] = min;
        }
        
    return m[1, n];
}
```
