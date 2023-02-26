# 자료구조

<details>
<summary><strong>💡 자료구조와 알고리즘의 차이</strong></summary>
  <ul>
    <li>자료구조는 데이터를 원하는 규칙 또는 목적에 맞게 저장하기 위한 구조이다.</li>
    <li>알고리즘이란 자료구조에 쌓인 데이터를 활용해 어떠한 문제를 해결하기 위한 여러 동작들의 모임이다.</li>
	</ul>
</details>
<details>
<summary><strong>💡 ArrayList와 LinkedList</strong></summary>
  <ul>
    <li>
      ArrayList는 배열은 연결된 데이터를 순차적으로(Ordered) 메모리상에 위치하는 배열의 형태를 가진다.
      <ul>
	      <li>인덱스로 데이터에 접근하기 때문에, 읽기 속도가 빠르다.</li>
  	    <li>크기가 정적으로 결정(Pre-Allocation)된다. 때문에 동적 Resizing이 필요한 경우 작업이 크게 늘어날 수 있다.</li>
	      <li>삽입 및 삭제 시, 연속적인 형태를 맞추기 위한 연산의 비용이 크다.</li>
  	  </ul>
    </li>
    <li>
      LinkedList는 각 노드가 데이터와 포인터를 갖고 한 줄로 연결되어 있는 형태로 데이터가 저장되는 자료구조이다.
      <ul>
	      <li>특정 값을 읽기 위해서는 리스트 전체를 순회해야 하기 때문에, 읽기 속도가 비교적 느리다.</li>
  	    <li>리스트 크기에 영향 없이, 값을 추가하고 삭제할 수 있다.</li>
    	  <li>삽입 및 삭제 시, 각 노드의 포인터를 연결하고 끊으면 되기 때문에 속도가 빠르다.</li>
	    </ul>
    </li>
	</ul>
</details>

<details>
<summary><strong>💡 List와 Set의 차이</strong></summary>
  <ul>
    <li>
      List는 중복이 허용되지만, Set은 중복이 허용되지 않는다.
      <ul>
	      <li>List의 데이터를 Set에 삽입하면, 중복이 제거된다.</li>
  	  </ul>
    </li>
    <li>
      Set은 고유성이 보장된다.
      <ul>
	      <li>DB의 <code>distict</code> 연산을 하는 효과를 갖는다.</li>
	    </ul>
    </li>
	</ul>
</details>

<details>
<summary><strong>💡 큐와 스택의 차이</strong></summary>
  <ul>
    <li>
      큐(Queue)
      <ul>
	      <li>
          선입선출(FIFO)
          <ul>
            <li>삽입연산(Enqueue)이 일어나는 곳은 Back(혹은 Rear)</li>
            <li>삭제연산(Dequeue)이 일어나는 곳은 Front</li>
          </ul>
        </li>
  	    <li>
        	구현
          <ul>
            <li>Array로 구현하면 poll 연산 이후 객체를 앞당기는 작업이 필요하다.</li>
            <li>Linked List로 구현하면 객체 한개만 제거하면 된다. <br>그러므로, 삽입 및 삭제가 용이한 LinkedList로 구현하는 것이 좋다.</li>
          </ul>
        </li>
  	  </ul>
    </li>
    <li>
      스택(Stack)
      <ul>
	      <li>
          후입선출(LIFO)
          <ul>
            <li>정해진 방향(top)으로만 데이터가 쌓이는 형태를 갖는다.</li>
            <li>정해진 방향(top)으로만 데이터가 삽입되고, 삭제된다.</li>
          </ul>
        </li>
  	    <li>
        	구현
          <ul>
            <li>List로 구현하면 객체를 제거하는 작업이 필요하다.</li>
            <li>Array로 구현하면 삭제할 필요 없이 index를 줄이고 초기화만 하면 되므로, Array로 구현하는 것이 좋다.</li>
          </ul>
        </li>
	    </ul>
    </li>
	</ul>
</details>
<details>
<summary><strong>💡 해시 테이블이란?</strong></summary>
  <ul>
    <li>해시 테이블은 (key,value) 형식으로 데이터를 저장하는 자료구조 중 하나로 빠른 데이터 검색이 필요할 때 유용하다.</li>
    <li>해시 테이블은 key 값에 해시 함수를 적용해 고유한 index를 생성하여 그 index에 저장된 값을 꺼내오는 구조이다.</li> 
    <li>해시 테이블은 key-value 가 1:1 로 매핑되어 있기 때문에 검색, 삽입, 삭제 과정에서 모두 평균적으로 O(1)의 시간 복잡도를 갖는다.</li>
	</ul>
</details>
<details>
<summary><strong>💡 연결 리스트란?</strong></summary><ul>
    <li>각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어있는 방식으로 데이터를 저장하는 자료구조</li>
    <li>각 노드는 다음 노드를 가리키는 포인터 포함</li>
    <li>→ 다음 노드를 가리키는 포인터 : 다음 노드의 주소를 값으로 가짐</li>
	</ul>
</details>

<details>
<summary><strong>💡 BST와 Binary Tree의 차이점은?</strong></summary>
  <ul>
    <li>
      이진트리(Binary Tree)
      <ul>
	      <li>
          자식노드가 최대 두개인 노드들로 구성되었다.
          <ul>
            <li>왼쪽 자식노드</li>
            <li>오른쪽 자식노드</li>
          </ul>
        </li>
  	    <li>자료 삽입, 삭제 방법에 따라 종류가 나뉜다.</li>
  	  </ul>
    </li>
    <li>
      이진 탐색 트리(Binary Search Tree)
      <ul>
	      <li>
          모든 왼쪽 자식노드 값이 루트나 부모 노드보다 작고, 모든 오른쪽 자식노드 값이 루트나 부모노드보다 크다.
        </li>
  	    <li>
          이진트리에 비해 탐색 속도가 빠르다. (<code>O(h)</code>, h는 트리의 높이)
        </li>
        <li>
          균형 잡힌 트리가 아닌 경우, 한쪽으로 쏠린 모양이 나타날 수 있다.
          <ul>
            <li>이 경우, 이진트리보다 탐색 속도가 느려진다. (<code>O(n)</code>)</li>
            <li>이를 위해 설계된 자료구조가 AVL Tree 이다.</li>
            <li>해당 문제 해결을 위해, 삽입과 삭제 시 트리 구조를 재조정하는 알고리즘을 추가할 수 있다.</li>
          </ul>
        </li>
	    </ul>
    </li>
	</ul>
</details>


<details>
<summary><strong>💡 BST의 문제점과 해결방안</strong></summary><ul>
    <li>문제점: 이진 탐색 트리(BST)는 Skewed Tree(편향된 트리)가 될 수 있으며, 이로 인해 평균 탐색 연산이 최악의 경우 O(n)의 시간 복잡도를 갖게 된다.</li>
    <li>해결방안: AVL Tree, Red-Black Tree와 같은 Balanced Binary Search Tree(균형 탐색 트리) 자료구조를 사용할 수 있다.</li>
	</ul>
</details>

<details>
<summary><strong>💡 Red Black Tree란?</strong></summary>
  <ul>
    <li>
    	레드 블랙 트리는 자기 균형 이진 탐색 트리(Self-Balancing BST)이다.
    </li>
    <li>
    	 이진탐색 트리에서의 조회 시간 복잡도는 <code>O(log n)</code>이 소요되나, 균형이 무너질 경우 <code>O(n)</code>으로 시간 복잡도가 증가할 수 있습니다. 이를 보완하기 위해 레드 블랙 트리에서는 삽입, 삭제 동안 트리의 모양의 균형을 이루도록 각 노드에 red와 black 색상을 가지도록 설계되었다.
    </li>
    <li>
			결과적으로 레드 블랙 트리는 자기 균형을 이루고 있기 때문에 검색, 삽입, 삭제 연산 시 worst case에서도 <code>O(log n)</code>의 시간 복잡도를 보장한다.
		</li>
    <img src="https://user-images.githubusercontent.com/70627979/221402026-96e8ef11-a332-4971-9b4b-24e5d550785b.png" alt="image" style="zoom:100%;" />
  </ul>
</details>


<details>
<summary><strong>💡 그래프와 트리의 차이점은?</strong></summary>
  <img width="564" alt="image" src="https://user-images.githubusercontent.com/70627979/218324529-b9bc059f-8dbf-4967-86dd-87f297ad7ba0.png">
</details>

<details>
<summary><strong>💡 트리 순회의 순서(전위, 중위, 후위)</strong></summary>
	<ul>
    <li>전위 순회는 [루트 → 왼쪽 자식 → 오른쪽 자식] 순으로 순회</li>
    <li>중위 순회는 [왼쪽 자식 → 루트 → 오른쪽 자식] 순으로 순회</li>
    <li>후위 순회는 [루트 → 왼쪽 자식 → 오른쪽 자식] 순으로 순회</li>
	</ul>
</details>
<details>
<summary><strong>💡 힙의 삭제 연산 과정을 설명해주세요</strong></summary>
	<ul>
    <li>
      힙이란 최댓값 또는 최솟값을 찾아내는 연산을 쉽게하기 위해 고안된 구조이다.
      <ul>
        <li>최대 힙: 각 노드의 키 값이 자식의 키 값보다 작지 않음</li>
        <li>최소 힙: 각 노드의 키 값이 자식의 키 값보다 크지 않음</li>
      </ul>
    </li>
    <li>
      루트 노드의 값이 가장 먼저 삭제된다.
      <ul>
        <li>최대 힙 : 최대값부터 삭제됨</li>
        <li>최소 힙 : 최소값부터 삭제됨</li>
      </ul>
    <ol>
    <li>루트 노드가 삭제</li>
    <li>마지막 노드가 루트 노드의 자리로 이동</li>
    <li>
    	힙의 종류 별로, 루트노드에 알맞은 값이 와야함
      <ul>
        <li>최대힙은 최대값, 최소힙은 최소값</li>
        <li>때문에, 재구조화 과정이 발생</li>
      </ul>
    </li>
  </ol>
	</ul>
</details>

<details>
<summary><strong>💡 우선순위 큐의 내부 구조를 설명해주세요.</strong></summary>
	<ul>
    <li>우선순위 큐란 Input 순서에 상관 없이, 우선순위가 높은 데이터를 먼저 Output하기 위해 고안된 자료구조이다.</li>
    <li>
      구현방법
      <img src="/Users/kanghyun/Library/Application Support/typora-user-images/image-20230207175711226.png" alt="image-20230207175711226"/>
    </li>
    <li>
    	배열과 리스트
      <ul>
        <li>데이터의 삽입, 삭제 과정의 비효율성</li>
        <li>삽입 위치를 찾기 위해 모든 데이터와 우선 순위를 비교해야함</li>
      </ul>
    </li>
    <li>
    	힙
      <ul>
        <li>Worst Case 임에도 시간 복잡도 O(log n)을 보장</li>
        <li>완전 이진트리 형태이기 때문</li>
      </ul>
    </li>
    ⇒ 우선순위 큐는 힙으로 구현됨
  </ul>
</details>
<details>
<summary><strong>💡 Binary Heap이란?</strong></summary>
	Binary Heap은 Tree 형식을 하고 있으며, Tree 중 배열을 기반으로 하는 완전 이진 트리(Complete Binary Tree) 이다. 힙에는 최대 힙(max heap)과 최소 힙(min heap) 두 종류가 있다.
  <ul>
    <li>
    	최대 힙은 각 노드의 값이 해당 자식의 값보다 크거나 같은 완전 이진 트리를 말한다.
    </li>
    <li>
			최소 힙은 최대 힙과 반대되는 개념으로 각 노드의 값이 해당 자식의 값보다 작은 완전 이진 트리를 말한다.
    </li>
    <li>
      배열을 기반으로 하는 Binary Tree의 값을 넣을 때, 1번 index부터 루트 노드가 시작된다. 0번 index를 건너뛰는 이유는 노드의 고유 번호 값과 배열의 index를 일치시켜 혼동을 줄이기 위함이다.
    </li>
  </ul>
  <img src="https://user-images.githubusercontent.com/70627979/221401328-145ba7bd-7d2f-49db-8b35-435077393d4a.png" alt="image" style="zoom:40%;" />
</details>
