# 알고리즘

<details>
<summary><strong>💡 DFS와 BFS의 차이점</strong></summary>
  <ul>
    <li>
      DFS
      <ul>
  			<li>깊이 우선 탐색 알고리즘(Depth-First-Search) : 그래프의 너비를 우선적으로 탐색하는 알고리즘</li>
		    <li>현재 정점에서 갈 수 있는 점들까지 들어가며 탐색하는 방식</li>
	  	  <li>스택 또는 재귀함수로 구현</li>
		  </ul>
    </li>
	  <li>
      BFS
      <ul>
	  	  <li>너비 우선 탐색 알고리즘(Breath-First-Search) : 그래프의 깊이를 우선적으로 탐색하는 알고리즘</li>
	    	<li>현재 정점에 연결된 가까운 점들부터 탐색하는 방식</li>
		    <li>큐를 이용해 구현</li>
		  </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 다이나믹 프로그래밍이란 무엇인지</strong></summary>
  <ol>
    <li>큰 문제를 작은 문제로 나눌 수 있다.</li>
    <li>작은 문제에서 구한 정답은 그것을 포함하는 큰 문제에서도 동일하다.</li>
    → 위 두 조건을 만족할 때 사용할 수 있는 알고리즘
  </ol>
  <ul>
    <li>
      Top-Down 방식
      <ul>
   	   <li>대부분 재귀함수를 사용해 구현</li>
   	   <li>큰 문제를 해결하기 위해 작은 문제를 호출하는 방식</li>
   	   <li>메모이제이션 : Top-Down 방식에서 사용되며, 이전에 계산된 결과를 일시적으로 기록해두는 개념</li>
   	 </ul>
    </li>
    <li>
      Bottom-Up 방식
      <ul>
 	     <li>단순 반복문을 이용해 구현</li>
 	     <li>작은 문제부터 차근차근 답을 도출하는 방식</li>
 	     <li>DP 테이블 : Bottom-Up 방식에서 사용되는 결과 저장용 리스트이다.</li>
 	   </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 그리디 알고리즘</strong></summary>
  <ul>
    <li>그리디 알고리즘 : 현재 상황에서 지금 당장 좋은 것만 고르는 방법</li>
    <li>매 순간 가장 좋아보이는 것을 선택하며, 현재의 선택이 나중에 미칠 영향에 대해 고려하지 않음</li>
    <li>최적해를 구하는 데에 사용되는 근사적인 방법</li>
    <br>
    <li>그리디 알고리즘 필요 조건</li>
    <ol>
      <li>탐욕스러운 선택 속성 : 탐욕적인 선택이 안전해야 함. 탐욕적인 선택으로 최적해를 구할 수 있어야 함.</li>
      <li>최적 부분 구조 : 문제에 대한 최적해를 구하는 방법이 하위 부분 문제에 대해서도 최적의 해결 방법</li>
    </ol>
  </ul>
</details>

<details>
<summary><strong>💡 시간 복잡도와 공간 복잡도</strong></summary>
효율적인 알고리즘이란 작은 메모리 공간을 차지하면서 적은 시간 내에 주어진 임무를 정확히 수행하는 알고리즘이다. <br>
알고리즘을 평가할 때 수행시간과 메모리 사용량을 평가 기준으로 두는데, 이에 해당하는 사항을 각각 시간 복잡도와 공간 복잡도라고 한다. <br>
  <ul>
    <li>시간 복잡도(Time Complexity)</li>
    <ul>
      <li>특정 알고리즘이 어떤 문제를 해결하는데 걸리는 시간을 의미한다.</li>
      <li>데이터 개수가 n이라면 n에 대한 연산 횟수의 함수 T(n)를 구해서 시간 복잡도를 나타낸다.</li>
      <li>최선의 경우, 최악의 경우, 평균적인 경우의 연산 횟수를 구할 수 있는데, 보통 알고리즘의 성능을 최악의 경우로 평가한다.</li>
      <li>빅오 표기법 : T(n)의 최고차항의 차수에 O를 씌운 표기법이다.</li>
    </ul>
    <br>
    <li>공간 복잡도(Space Complexity)</li>
    <ul>
      <li>특정 알고리즘에 사용되는 메모리 공간의 총량을 의미한다.</li>
      <li>변수를 저장하기 위한 공간이나 순환 스택 등에 해당한다.</li>
      <li>대용량 시스템이 보편화되면서 중요도가 떨어졌다.</li>
    </ul>
  </ul>
</details>

<details>
<summary><strong>💡 정렬 알고리즘 시간복잡도</strong></summary>
  <img src="https://user-images.githubusercontent.com/70627979/213904153-b23c37c5-9978-47eb-a024-ad06db4ba0d0.png" alt="image" style="zoom:70%;" />
</details>