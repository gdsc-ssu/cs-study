# Monotone Stack



# Monotone Stack

시간복잡도 O(N)으로 각 원소는 최대 한 번 스택에 들어가고 최대 한 번 스택에서 빠져나오면서 내용물의 오름차순 혹은 내림차순 상태를 유지한다. → 몇몇의 문제의 경우 시간 복잡도를 O(N)으로 줄여줄 수 있기 때문에 알고리즘문제를 풀 때 중요한 테크닉이 될 수 있다. 

## **개념**

스택의 **top**에 있는 숫자와 새롭게 들어오는 숫자를 비교하고, 경우에 따라 **pop** 하며 진행한다.

- **중복없는 오름차순 스택**인경우, 들어가려는 수가 top 보다 작거나 같은 경우 오름차순을 만족할 때까지 pop을 반복 한 후 push.
- **중복없는 내림차순 스택**인경우, 들어가려는 수가 top 보다 크거나 같은 경우 내림차순을 만족할 때까지 pop을 반복한 후 push.

# **활용법**

주어진 숫자중에서 어떤 숫자 x보다 왼쪽에 있는 숫자 중에서 처음으로 나오는 x보다 작은 수의 위치 혹은 값을 바로 알 수 있다. 또한,  **내림차순으로 / 중복을 허용 /인덱스와 함께 저정하거나 / 오른쪽부터 삽입**하는 등의 변형을 통해 더욱 다양한 정보를 얻을 수 있다. 

특정 원소를 제거해서 정렬해 **스택을 단조롭게 만드는 것이 핵심이다.** 

### 유사한 접근 방식

- Brute force

왼쪽에서 오른쪽으로 검사하는 방식이다.

역방향부터 검색하면서 오른쪽에 있는 값이 더 작다면 없애는 방식이다.

### 관련문제 - 백준

- 17298 오큰수
<
#include<iostream>
#include<algorithm>
#include<vector>
#include<stack>
 
using std::cout; using std::cin;
using std::vector;
 
int n;
int result[1000001];
 
int main() {
	std::ios::sync_with_stdio(false);
	cin.tie(nullptr); cout.tie(nullptr);
 
	std::stack<std::pair<int, int>> st;
	cin >> n;
 
	int cnt = 0;
	std::fill_n(result + 1, n, -1);  // result 배열 -1 로 초기화
 
	int size = n;
 
	while (n--) {
		int a;
		cin >> a;
		cnt++;
		
        // 오큰수 찾음.
		while (!st.empty() && st.top().first < a) {
			result[st.top().second] = a;
			st.pop();
		}
 
		st.push({ a,cnt });
	}
	// 스택에 남아있는 값은 오큰수가 없는 값. 고로 그대로 -1 출력.
	for (int i = 1; i <= size; i++) {
		cout << result[i] << " ";
	}
 
	return 0;
}
>
해당 문제 코드를 참고해보세요.

- 1725 히스토그램
- 5828 Fuel Economy

### 핵심 아이디어

- [https://justicehui.github.io/medium-algorithm/2019/01/01/monotoneStack/](https://justicehui.github.io/medium-algorithm/2019/01/01/monotoneStack/)
