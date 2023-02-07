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
<summary><strong>💡 BST의 문제점과 해결방안</strong></summary><ul>
    <li>문제점: 이진 탐색 트리(BST)는 Skewed Tree(편향된 트리)가 될 수 있으며, 이로 인해 평균 탐색 연산이 최악의 경우 O(n)의 시간 복잡도를 갖게 된다.</li>
    <li>해결방안: AVL Tree, Red-Black Tree와 같은 Balanced Binary Search Tree(균형 탐색 트리) 자료구조를 사용할 수 있다.</li>
	</ul>
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
			<li>최대 힙 삭제 과정</li/>
			<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1893b9c8-97c3-4f7f-9b28-1031239898ef/max_heap_deletion_animation.gif?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230207%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230207T084545Z&X-Amz-Expires=86400&X-Amz-Signature=54efd328bc9bb3b1c910de9ebbaaa4059bccb6e147b065e6d029e9803d71632b&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22max_heap_deletion_animation.gif%22&x-id=GetObject" alt="image"/>
		</li>
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
