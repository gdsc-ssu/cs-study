# 🌵 이진탐색트리(Binary Search Tree)

## 🌵 이진탐색트리(Binary Search Tree)란 무엇일까?

- 이진탐색트리는 `이진탐색(Binary Search`와 `연결리스트(Linked List)`가 결합된 자료구조의 일종이다.
  - `이진탐색(Binary Search`의 효율적인 탐색 능력
  - `연결리스트(Linked List)`의 데이터 삽입/삭제 용이성
    - 일반 배열과 다르게 연결리스트는 **비연속적인 공간 할당**을 통해 메모리를 저장하기에 삽입/삭제 비용이 적다.
    - [GDSC SSU CS-Study 연결 리스트](https://github.com/gdsc-ssu/cs-study/blob/main/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0/Linked%20List.md) 참고
- 때문에, 기존의 `이진트리(Binary Tree)`보다 탐색 속도가 빠르다.
  - [GDSC SSU CS-Study 이진트리](https://github.com/gdsc-ssu/cs-study/blob/main/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0/BinaryTree.md) 참고
  - 트리의 높이가 **h**일 때, **`O(h)`** 의 시간 복잡도를 갖는다.

## 🌵 이진탐색트리(Binary Search Tree)의 연산

: 이진탐색트리의 핵심 연산은 `탐색(Search)` `삽입(Insert)` `삭제(Delete)`이다.

### 1️⃣ 탐색(Search)

```
1. 루트 노드의 키와 찾고자 하는 값을 비교한다. 만약, 루트 노드가 찾고자 하는 값이라면 탐색을 종료한다.
2. 찾고자 하는 값이 루트 노드의 키보다 작다면, 왼쪽 서브 트리로 탐색을 진행한다.
3. 찾고자 하는 값이 루트 노드의 키보다 크다면, 오른쪽 서브 트리로 탐색을 진행한다.
4. 값을 찾을 때 까지 위의 과정을 반복하며, 값을 찾지 못한다면 종료한다.
```

- 아래의 그림을 통해 이진탐색트리의 탐색 과정을 살펴보자.<br/>
  ![image](https://i.imgur.com/SSusVoP.png)<br/>
- `10`을 탐색하는 경우
  - **7 > 8 > 10**
- `4`를 탐색하는 경우
  - **7 > 3 > 5**
  - 리프 노드까지 도달했으나, 값을 찾지 못했다.
  - 서브 트리가 존재하지 않기에, 값을 찾지 못하고 탐색을 종료.

> 위의 과정에서, 반드시 **`트리의 높이(h)` 이하**의 탐색이 이루어진다.<br/>최악의 경우 리프 노드까지 탐색해야하기 때문이다.

```python
    def find(self, val):
        if (self.findNode(self.root, val) is False):
            return False
        else:
            return True

    def findNode(self, currentNode, val):
        if (currentNode is None):
            return False
        elif (val == currentNode.val):
            return currentNode
        elif (val < currentNode.val):
            return self.findNode(currentNode.leftChild, val)
        else:
            return self.findNode(currentNode.rightChild, val)
```

### 2️⃣ 삽입(Insert)

```
1. 삽입할 값을 루트 노드와 비교한다.
    - 값이 루트 노드와 같다면 에러.
    - 중복 값은 허용되지 않는다.
2. 삽입할 값이 루트 노드의 키보다 작다면, 왼쪽 서브 트리를 탐색한다.
    - 비어있다면 추가한다.
    - 비어있지 않다면, 다시 값을 비교한다.
3. 삽입할 값이 루트 노드의 키보다 크다면, 오른쪽 서브 트리를 탐색한다.
    - 비어있다면 추가한다.
    - 비어있지 않다면, 다시 값을 비교한다.
```

- 아래의 그림을 통해 이진탐색트리의 탐색 과정을 살펴보자.<br/>
  ![image](https://i.imgur.com/SSusVoP.png)<br/>
  - 위의 트리에, `4`를 삽입(Insert)하는 경우 아래의 그림과 같은 트리가 그려진다.<br/>
    ![image](https://i.imgur.com/HBthwOc.png)<br/>
  - 🙄 `4`가 `7`과 `3` 사이에 삽입되어도 괜찮지 않을까?
    - **NO!** 트리의 중간에 데이터를 삽입하면 서브 트리의 속성이 깨질 수 있다.
    - **때문에 삽입(Insert)은 반드시 리프 노드에서만 이루어진다.**
- 위와 같은 삽입(Insert) 과정의 특징 때문에, 트리의 최소값과 최대값을 쉽게 찾을 수 있다.
  - 트리의 가장 왼쪽 리프 노드는 해당 트리의 최소값이 된다.
  - 트리의 가장 오른쪽 리프 노드는 해당 트리의 최대값이 된다.

```python
    def insert(self, val):
        if (self.root is None):
            self.setRoot(val)
        else:
            self.insertNode(self.root, val)

    def insertNode(self, currentNode, val):
        if (val <= currentNode.val):
            if (currentNode.leftChild):
                self.insertNode(currentNode.leftChild, val)
            else:
                currentNode.leftChild = Node(val)
        elif (val > currentNode.val):
            if (currentNode.rightChild):
                self.insertNode(currentNode.rightChild, val)
            else:
                currentNode.rightChild = Node(val)
```

### 3️⃣ 삭제 (Delete)

: 이진탐색트리(Binary Search Tree)에서 `삭제(Delete)`의 과정은 세 가지 상황을 나누어 구현한다.<br/>

> 서브 트리에서 이진탐색트리의 속성이 깨질 수 있기 때문이다.

#### 🐸 삭제하려는 노드가 리프 노드인 경우

- 삭제하려는 노드가 자식 노드가 없는 `리프 노드`인 경우의 삭제 방법이다.
  1. 부모 노드가 있다면, 부모 노드의 자식을 `null`로 만든다.
  2. 삭제할 노드를 삭제한다.
     - 메모리 해제

#### 🐸 삭제하려는 노드의 서브 트리가 하나인 경우

![image](https://i.imgur.com/RqCRxO9.png)

- 삭제하려는 노드에 하나의 서브 트리가 존재하는 경우의 삭제 방법이다.
  1. 삭제할 노드의 자식 노드를, 삭제할 노드의 부모 노드가 가리키게 한다.
  2. 삭제할 노드를 삭제한다.
     - 메모리 해제
- 삭제할 노드의 자식 노드는, 삭제할 노드의 부모 노드보다 **작거나 같다.**
  - 이진탐색트리의 특성 때문이다.
  - **삭제로 인해 이진탐색트리의 속성이 깨지지 않는다.**

#### 🐸 삭제하려는 노드의 서브 트리가 두개인 경우

: **두 가지 방법**이 존재한다.

1. 삭제할 노드의 왼쪽 서브 트리의 가장 큰 자손(**`predecessor`**)을 해당 노드의 자리에 올린다.<br/>
   ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FbcTUrX%2Fbtq92Q1tw0m%2FtyYJcuLUtWj7kD5k3qAeMK%2Fimg.png)<br/>
   - 그림에서 루트 노드의 왼쪽 서브 트리 속 가장 큰 자손은 `5`번 노드이다.
   - `5`번 노드를 루트 노드로 올려도, **이진탐색트리의 속성이 깨지지 않는다.**
   - `5`번 노드가 자리를 옮기면서 `4`번 노드와 같은 다른 노드의 위치가 적절히 변경된다.
2. 삭제할 노드의 오른쪽 서브 트리의 가장 작은 자손(**`successor`**)을 해당 노드의 자리에 올린다.<br/>
   ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FbI3IEY%2Fbtq9Rc54r92%2FnDvEWCXdq9qVmYaYiHKAAK%2Fimg.png)<br/>
   - 그림에서 루트 노드의 오른쪽 서브 트리 속 가장 작은 자손은 `8`번 노드이다.
   - `8`번 노드를 루트 노드로 올려도, **이진탐색트리의 속성이 깨지지 않는다.**
   - `8`번 노드가 자리를 옮기면서 `10`번 노드와 같은 다른 노드의 위치가 적절히 변경된다.

```python
def delete_Node(root, key):
  # 루트 노드가 없는 경우
	if not root:
		return root
    # 값이 루트 노드보다 작다면, 왼쪽 서브 트리를 탐색.
	if root.val > key:
		root.left = delete_Node(root.left, key)
    # 값이 루트 노드보다 크다면, 오른쪽 서브 트리를 탐색.
	elif root.val < key:
		root.right= delete_Node(root.right, key)
	# root.value == key 인경우, 노드 삭제.
	else:
    # 오른쪽 자식이 없다면, 해당 노드를 지우고 root.right가 새 루트 노드가 된다.
		if not root.right:
			return root.left
    # 왼쪽 자식이 없다면, 해당 노드를 지우고 root.left가 루트 새 노드가 된다.
		if not root.left:
			return root.right
  # 삭제할 노드의 오른쪽 서브 트리의 가장 작은 자손을 해당 노드의 자리에 올린다.
		temp_val = root.right
		mini_val = temp_val.val
		while temp_val.left:
			temp_val = temp_val.left
			mini_val = temp_val.val
  # 오른쪽 서브 트리의 가장 작은 자손을 삭제.
		root.right = deleteNode(root.right,root.val)
	return root
```

## 🌵 이진탐색트리(Binary Search Tree) 시간 복잡도

- 최악의 경우는, **자식이 두개인 노드를 삭제하는 경우이다.**
  - 트리의 높이가 `h`이고, 삭제할 노드의 레벨이 `d`라고 가정한다.
  - 삭제할 노드의 왼쪽(혹은 오른쪽) 서브 트리를 찾기 위한 **`d`번의 비교 과정**
  - `predecessor`(혹은 `successor`)를 찾기 위해 **삭제할 노드의 높이인 `h-d`번의 비교 과정**
  - 결국 O(d + h - d), 즉 **O(h)** 가 시간 복잡도.

## 🌵 이진탐색트리(Binary Search Tree)의 한게점

- 이진탐색트리(Binary Search Tree)의 `탐색(Search)` `삽입(Insert)` `삭제(Delete)` 과정의 시간 복잡도는 모두 **O(h)** 이다.<br/>
  ![image](https://i.imgur.com/XR4fujQ.png)
  - 위의 그림은, 노드 수가 적지만 높이가 `4`이다.
  - 노드가 일렬로 세워져 높이가 `n`이 되는 경우도 이진탐색트리가 된다.
    - 이 경우엔 시간 복잡도가 **O(n)** 이 된다.
    - 🙄 탐색 속도가 **O(log n)** 인 `이진탐색`보다 느려질 수 있다.
    - 😭 `이진탐색`을 계승했다면서요...
  - 때문에 트리의 입력/삭제 단계에 트리 전체의 균형을 맞추는, 이진탐색트리의 일종인 **`AVL Tree`** 가 제안되었다.

## 🔍 참고자료

### 내용 및 이미지 참고

- [이진탐색트리(Binary Search Tree)](https://ratsgo.github.io/data%20structure&algorithm/2017/10/22/bst/)
- [[자료구조] 이진탐색트리(Binary Search Tree)의 개념, 이해 | C언어 이진탐색트리 구현](https://code-lab1.tistory.com/10#recentComments)

### 소스코드 참고

- [이진탐색트리(Binary Search Tree)](https://ratsgo.github.io/data%20structure&algorithm/2017/10/22/bst/)
- [Python Binary Search Tree: Delete a node in a given Binary search tree (BST)](https://www.w3resource.com/python-exercises/data-structures-and-algorithms/python-binary-search-tree-exercise-4.php)
