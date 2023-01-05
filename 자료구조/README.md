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
    <li>ArrayList는 배열은 연결된 데이터를 순차적으로(Ordered) 메모리상에 위치하는 배열의 형태를 가진다.</li>
    <ul>
      <li>인덱스로 데이터에 접근하기 때문에, 읽기 속도가 빠르다.</li>
      <li>크기가 정적으로 결정(Pre-Allocation)된다. 때문에 동적 Resizing이 필요한 경우 작업이 크게 늘어날 수 있다.</li>
      <li>삽입 및 삭제 시, 연속적인 형태를 맞추기 위한 연산의 비용이 크다.</li>
    </ul>
    <li>LinkedList는 각 노드가 데이터와 포인터를 갖고 한 줄로 연결되어 있는 형태로 데이터가 저장되는 자료구조이다.</li>
    <ul>
      <li>특정 값을 읽기 위해서는 리스트 전체를 순회해야 하기 때문에, 읽기 속도가 비교적 느리다.</li>
      <li>리스트 크기에 영향 없이, 값을 추가하고 삭제할 수 있다.</li>
      <li>삽입 및 삭제 시, 각 노드의 포인터를 연결하고 끊으면 되기 때문에 속도가 빠르다.</li>
    </ul>
	</ul>
</details>