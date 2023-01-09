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