# Balanced Binary Search Tree (균형 탐색 트리)

이진 탐색 트리는 Skewed Tree(편향된 트리)가 될 수 있고, 이러한 문제 때문에 최악의 경우 시간복잡도가 O(n)까지 떨어지는 문제점이 있다. 이 문제를 해결하기 위해 균형잡힌 트리를 위한 자료구조 AVL Tree, Red-Black Tree가 존재한다. 두 자료구조는 균형이 잡힌 트리 구조이기 때문에 시간 복잡도가 O(logN)이 된다.

<br>

## AVL Tree

AVL Tree는 BST를 기반으로 하는 트리 형식의 자료구조이며, 모든 노드에 대해 **좌측 서브 트리의 높이와 우측 서브 트리의 높이의 차이가 1 이하인 트리이다.**

즉, 아래 이미지와 같이 서브트리의 높이 차가 2 이상이 나는 경우, AVL 트리가 아니므로 균형을 맞추는 과정이 필요하다.

<img width="313" alt="image" src="https://user-images.githubusercontent.com/70627979/171010595-7cd2145a-47b5-440f-8b8f-5b048a7a8ff5.png" style="zoom:50%;" >



### 균형 맞추기

AVL Tree의 균형을 맞추기 위해 불균형이 발생한 서브 트리를 좌회전 (Left Rotation), 우회전 (Right Rotation) 시키는 방법이 존재한다. 상황에 따라 좌회전, 우회전 중 하나를 선택하거나 두 가지를 모두 사용해야하는 경우가 있기 때문에, 불균형이 발생한 유형을 4가지로 구분하고 그에 맞는 해결 방법을 선택하여 트리의 균형을 맞춰야 한다.

<img width="805" alt="image" src="https://user-images.githubusercontent.com/70627979/171013213-62412e9c-a06d-4967-8a7c-fe683d80ba25.png" style="zoom: 50%;" >



#### 4가지 유형

(t: 불균형이 발생한 서브트리의 루트)

- LL 유형: t.left.left 가 가장 깊음
- LR 유형: t.left.right 가 가장 깊음
- RL 유형: t.right.left 가 가장 깊음
- RR 유형: t.right.right 가 가장 깊음



#### 해결 방법

- LL 유형: 우회전
- LR 유형: 좌회전(LL로 변환) 후 우회전 
- RL 유형: 우회전(RR로 변환) 후 좌회전
- RR 유형: 좌회전



<br>

## Red-Black Tree (레드-블랙 트리)

RBT(Red-Black Tree)는 BST를 기반으로 하는 트리 형식의 자료구조이며, 레드와 블랙 색상을 사용해 균형을 맞춘 트리이다.



### 특성

- **Root Node: Black**

- **Leaf Node: Black**

- **Red의 자식 노드: Black** (즉, Red가 연속으로 나올 수 없음)

- **모든 Leaf Node의 Black Depth가 같음** (즉, 루트노드에서 각 리프노드까지 이어지는 노드 중 Black 개수는 모두 동일하다)



### 삽입

**삽입되는 노드의 색깔은 Red이다.**

이진 탐색 트리 방식으로 삽입을 계속 진행하다보면, 빨간 노드가 연달아 나올 수 없다는 규칙을 어기게 된다. (이를 Double Red라 함)
규칙을 지키면서 삽입을 하기 위해 삽입 후, 상황에 따라 **Restructuring** 또는 **Recoloring**을 해야 한다.



- Parent Node의 색상이 블랙인 경우 

  → RB 특성을 만족하므로, 그대로 종료

- Parent Node의 색상이 레드인 경우
  - Uncle Node의 색상이 **블랙**(or Null)인 경우 → **Restructuring**
  - Uncle Node의 색상이 **레드**인 경우 → **Recoloring**

(Uncle Node: 부모 노드의 형제 노드, 삼촌 노드)

<img src="https://user-images.githubusercontent.com/70627979/149765431-b5a244b0-114a-4f93-bc2a-cc445ee10e42.png" alt="image" style="zoom: 67%;" />

(삽입 노드: X, 부모 노드: P, 부모의 부모 노드: P2, 삼촌 노드: U)



#### Recoloring의 동작 방식

1. P와 U를 블랙으로 변경, P2를 레드로 변경
2. P2가 Root Node가 아닌 경우, Doubled Red가 다시 발생할 수 있으며 이런 경우 P2가 새롭게 삽입된 것으로 생각하여 재귀적으로 해결

<img src="https://user-images.githubusercontent.com/70627979/149768757-4e3f34ea-8a05-436f-9dcb-5cdc4f41fb81.png" alt="image" style="zoom:67%;" />



#### Restructuring 동작 방식

- X가 P의 오른쪽 자식인 경우 (case1)

  1. P를 중심으로 좌회전(Left Rotation)
  2. case2로 변함

- X가 P의 왼쪽 자식인 경우 (case2)

  1. P2를 중심으로 우회전
  2. P와 P2의 색상을 맞바꿈
  3. 종료

  

- Restructuring은 다음과 같은 방식으로도 가능하다.

  1. X, P, P2를 오름차순으로 정렬

  2. 가운데 있는 값을 부모 노드로 만들고, 나머지 두 노드를 자식 노드로 만든다.
  3. 부모 노드를 블랙, 자식 노드들을 레드로 만든다.

  <img src="https://user-images.githubusercontent.com/70627979/149768820-473e3f41-1291-43db-8b8f-c5b1d54c1aff.png" alt="image" style="zoom:67%;" />





### 삭제

삭제도 마찬가지로 RBT의 규칙을 지키면서 진행해야 한다. 

만약 삭제할 노드가 빨간색이라면 해당 노드를 삭제하면 되지만, 삭제할 노드가 검정색인 경우 모든 Leaf Node의 Black Depth가 같다는 규칙을 지키기 위해 Black-Height가 감소한 경로에 검정색 노드가 하나 추가되도록 rotation하고 노드의 색상을 변경해야 한다.

<br>

## 참고 자료

- https://zeddios.tistory.com/237
- https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/DataStructure#red-black-tree
- https://nesoy.github.io/articles/2018-08/Algorithm-RedblackTree