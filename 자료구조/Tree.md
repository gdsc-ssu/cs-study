# 🎄 트리 (Tree)

> 트리(Tree)는 계층적인 자료를 표현할 때 사용되는 **비선형 계층적 자료구조** 입니다.

## 🌳 트리구조(Tree)란 무엇일까?

- **그래프(Graph)** 의 일종이다.
- 한 노드에서 시작해서 다른 정점들을 순회하여 자기 자신에게 돌아오는, 순환이 없는 **무방향 연결 그래프** 이다.
- 트리구조 내에 또 다른 하위 트리구조가 존재할 수 있는, **재귀적 자료구조** 이기도 하다.
- 대표적으로, 컴퓨터의 <span style="color:red">`directory`</span>구조나 <span style="color:red">`기업 및 정부 조직도`</span>가 트리구조이다.
- **가지를 늘려가며 뻗어나간다.**
  <br/>
  ![image](https://user-images.githubusercontent.com/44965706/198544233-12062c2f-f653-4b58-9766-bf731d79744a.png)<br/>
  _나무를 뒤집어놓은 듯한 모습이다_

## 🌳 트리구조(Tree) 용어

> 트리구조에서 사용되는 용어입니다.

| 용어                                                      | 의미                                                         |
| --------------------------------------------------------- | ------------------------------------------------------------ |
| 노드(<span style="color:red">`node`</span>)               | 가장 기본적인 트리의 구성요소. 위 그림의 각 숫자에 해당한다. |
| 간선(<span style="color:red">`edge`</span>)               | 노드와 노드를 연결하는 연결선.                               |
| 루트 노드(<span style="color:red">`root node`</span>)     | 트리 구조에서 최상위에 존재하는 노드.                        |
| 단말 노드(<span style="color:red">`terminal node`</span>) | 아래로 또 다른 노드가 연결되어 있지 않은 노드.               |
| 내부 노드(<span style="color:red">`internal node`</span>) | 단말 노드를 제외한 모든 노드.                                |

- 단말 노드(<span style="color:red">`terminal node`</span>)는 잎사귀 노드(<span style="color:red">`leaf node`</span>)라고도 불린다.
- 내부 노드(<span style="color:red">`internal node`</span>)는 비단말 노드(<span style="color:red">`nonterminal node`</span>)라고도 불린다.
- 노드간 관계가 성립될 수 있다.
  - <span style="color:red">`부모(parent)`</span>
  - <span style="color:red">`자식(child)`</span>
  - <span style="color:red">`형제(sibling)`</span>
  - <span style="color:red">`조상(ancestor)`</span>
  - <span style="color:red">`gnths(descendant)`</span>

## 🌳 트리구조(Tree)의 특징

> **하나의 루트노드**에 **0개 이상의 자식노드**로 이루어져 있습니다.

- 모든 자식 노드는 하나의 부모 노드를 갖습니다.
- 노드가 **n개**인 트리는 항상 **n-1개**의 간선을 갖습니다.

### 👍 트리구조 맞습니다.

- ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FvKvqg%2Fbtq1E9ODRk8%2FqXL8GehaRh0tgxiyrm8Q31%2Fimg.png)<br/>

### 👎 트리구조 아닙니다.

- ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsXGwq%2Fbtq1ByPsA98%2FiAmWtKVq4WWdEV85sorkkk%2Fimg.png)<br/>
  - _루트노드가 두개이기 때문이다._<br/>
- ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F4pwtu%2Fbtq1By9I93O%2Fzz7ZRsYNpUbKfCwCf0Jno0%2Fimg.png)<br/>
  - _6번 노드의 부모노드가 두개이기 때문이다._
  - _cycle을 이루기 때문이다._

## 🌳 트리구조(Tree)의 종류

> 5가지 트리구조를 살펴보겠습니다.

### 1️⃣ 편향트리 (Skew Tree)

- 모든 노드들이 하나의 자식을 가지는 트리구조.
  - 왼쪽으로 치우친 트리는 `left skew tree`
  - 오른쪽으로 치우친 트리는 `right skew tree`

### 2️⃣ 이진트리 (Binary Tree)

- 각 노드의 자식노드가 2개인 트리구조.

### 3️⃣ 이진 탐색 트리 (Binary Search Tree, BST)

- 순서화된 이진트리를 의미한다.
- 특정 노드의 왼쪽 자식은 해당 노드보다 **작은 값**을, 오른쪽 자식은 해당 노드보다 **큰 값**을 가져야한다.

### 4️⃣ m 원 탐색 트리(m-way search tree)

- 최대 m개의 서브트리를 갖는 탐색 트리
- `이진 탐색 트리`의 확장 버전.
  - 높이를 줄이기 위해 사용.

### 5️⃣ 균형 트리 (Balanced Tree, B-Tree)

- m원 탐색 트리에서 높이 균형을 유지하는 트리
  - `height-balanced m-way tree`

## 🌳 트리구조(Tree)의 순회

> 트리의 노드를 체계적으로 탐색하는 과정을 의미합니다. `전위 순회` `중위 순회` `후위 순회` `레벨 순회`로 나뉘어 있습니다.

### 1️⃣ 전위 순회 (Preorder)

- **깊이 우선 순회**라고도 불린다.
- 루트노드 --> 왼쪽 서브트리 --> 오른쪽 서브트리 순서로 순회하는 방식이다.
  - ![image](https://upload.wikimedia.org/wikipedia/commons/a/ac/Preorder-traversal.gif)<br/>
  ```python
  def preorder(self):
          def _preorder(node):
              print(node.item, end=' ')
              if node.left:
                  _preorder(node.left)
              if node.right:
                  _preorder(node.right)
          _preorder(self.root)
  ```

### 2️⃣ 중위 순회 (Inorder)

- **대칭 순회**라고도 불린다.
- 왼쪽 서브트리 --> 루트노드 --> 오른쪽 서브트리 순서로 순회하는 방식이다.
  - ![image](https://upload.wikimedia.org/wikipedia/commons/4/48/Inorder-traversal.gif)<br/>
  ```python
  def inorder(self):
  def _inorder(node):
      if node.left:
          _inorder(node.left)
      print(node.item, end=' ')
      if node.right:
          _inorder(node.right)
  _inorder(self.root)
  ```

### 3️⃣ 후위 순회 (Postorder)

- 왼쪽 서브트리 --> 오른쪽 서브트리 --> 루트노드 순서로 순회하는 방식이다.
  - ![images](https://upload.wikimedia.org/wikipedia/commons/2/28/Postorder-traversal.gif)<br/>
  ```python
  def postorder(self):
  def _postorder(node):
      if node.left:
          _postorder(node.left)
      if node.right:
          _postorder(node.right)
      print(node.item, end=' ')
  _postorder(self.root)
  ```

### 4️⃣ 레벨 순회 (Levelorder)

- **너비 우선 순회**라고도 불린다.
- 각 노드를 레벨 순서대로 검사하는 순회 방법이다.
- `스택`을 사용하던 위의 세가지 순회 방법과 다르게, `선입선출 기반의 큐`를 기반으로 한다.

  - ![image](https://res.cloudinary.com/practicaldev/image/fetch/s--Lng93Nkl--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/eijg2o9eo8xtqk40q91d.png)

  ```python
  from collections import deque

  def levelorder(self):
      q = deque([self.root])
      while q:
          node = q.popleft()
          print(node.item, end=' ')
          if node.left:
              q.append(node.left)
          if node.right:
              q.append(node.right)
  ```

> 내용 참고 : [윤성우의 열혈 자료구조](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php), [[자료구조] 트리 (Tree)](https://velog.io/@kimdukbae/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%ED%8A%B8%EB%A6%AC-Tree), [[자료구조] 트리 (Tree)](https://yoongrammer.tistory.com/68)

> 소스코드 참고 : [[Python] 트리 구현 / 순회(전위 순회, 중위 순회, 후위 순회, 레벨 순회)](https://koosco.tistory.com/109)
