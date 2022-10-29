# 🎄 이진트리 (Binary Tree)

> **트리구조(Tree)** 의 여러 유형 중 가장 기본이 되는 유형입니다.

_해당 문서는 [트리구조(Tree)](https://github.com/Jun99uu/TIL/blob/master/CS/data-structure/Tree.md)와 이어집니다._

## 🌴 이진트리(Binary Tree)란 무엇일까?

- 각 노드의 자식노드가 **2개 이하**인 트리구조.
  ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FblbjFV%2Fbtq1K3P9Y8v%2FH393OwoRI9lX8N3wrz9OO1%2Fimg.png)
- 자식 노드 중 **왼쪽 자식**을 `left node`, **오른쪽 자식**을 `right node`라고 한다.
  - `left node`에 의한 서브트리와 `right node`에 의한 서브트리는 확실하게 구분되어야 한다.

## 🌴 이진트리(Binary Tree)의 특징

- **n개**의 노드를 가진 이진트리는 항상 **(n-1)개**의 간선을 갖는다.
  - 루트노드를 제외한 모든 노드가 부모노드를 갖기 때문이다.
- 높이가 `h`인 이진트리가 가질 수 있는 노드의 최소 개수는 **(h+1)개**, 최대 개수는 **(2^(h+1) -1)개**이다.
  - 이진트리의 높이가 `h`가 되기 위해선, 한 레벨에 최소 한개의 노드가 있어야하기 때문이다. --> 최소 **(h+1)개**
  - 하나의 노드는 최대 2개의 자식 노드를 가질 수 있기 때문에 레벨 `i`에서 노드의 최대 개수는 **2^i**가 된다. --> 높이가 `h`일 때, 최대 노드의 개수는 **(2^(h+1) -1)개**

## 🌴 이진트리(Binary Tree)의 종류

> 이진트리(Binary Tree)의 4가지 유형을 소개합니다.

### 1️⃣ 정 이진트리 (Full Binary Tree or Strict Binary Tree)

- 모든 노드가 **0개** 혹은 **2개**의 자식 노드를 갖는 트리구조이다.
  ![images](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdSwyWw%2Fbtq9KmfrOlf%2F37ctrWKZKRSQJEZA7C9UMK%2Fimg.png)

### 2️⃣ 완전 이진 트리 (Complete Binary Tree)

- 마지막 레벨을 제외 하고 모든 레벨이 완전히 채워져 있는 트리구조.
- 마지막 레벨은 꽉 차 있지 않아도 되지만, 노드가 왼쪽에서 오른쪽으로 채워져야 한다.
- 마지막 `레벨 h`에서 **1 ~ 2h-1 개**의 노드를 가질 수 있다.
- 완전 이진 트리는 배열을 사용해 효율적으로 표현 가능하다.
  ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb7BofG%2Fbtq9Eilu1J5%2F0HNO2KiWkBxTvERSJGHla0%2Fimg.png)

### 3️⃣ 포화 이진 트리 (Perfect Binary Tree)

- 모든 레벨이 완전히 채워져 있는 트리구조.
- `정 이진트리 (Full Binary Tree or Strict Binary Tree)`의 성질도 만족해야 한다. 즉 모든 노드가 **0개** 혹은 **2개**의 자식 노드를 갖는다.
- 모든 말단 노드가 **동일한 깊이 또는 레벨**을 갖는다.
- 높이 `k`의 트리에서, 노드 개수가 정확히 **2^k-1 개**여야 한다.
  ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdfWC2R%2Fbtq9LqomTS7%2Frt4Io0pCfqBCckCs92CNz0%2Fimg.png)

### 4️⃣ 균형 이진 트리 (Balanced Binary Tree)

- 왼쪽 서브트리와 오른쪽 서브트리의 높이 차이가 모두 `1`만큼 나는 트리구조.
  ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcBpW7h%2Fbtq2E9oilQv%2F5r8K5dfuj56DKKniJh7tRk%2Fimg.png)

## 🌴 이진트리(Binary Tree) 구현

> 이진트리의 각 노드 인스턴스는 자신의 부모 노드에 대한 레퍼런스와 두 자식노드에 대한 레퍼런스를 가지게 됩니다.

```python
    # 이진트리의 노드
    class Node:
        def __init__(self, data):
            # 파라미터로 받은 데이터를 삽입
            self.data = data
            # None으로 초기값을 지정 후, 노드 생성 후에 지정
            self.left_child = None
            self.right_child = None
```

### 😀 예제 이진트리

```python
    node1= TreeNode()
    node1.data = 'apple'

    node2= TreeNode()
    node2.data = 'banana'
    node1.left = node2

    node3= TreeNode()
    node3.data = 'carrot'
    node1.right = node3

    node4= TreeNode()
    node4.data = 'donkey'
    node2.left = node4

    node5= TreeNode()
    node5.data = 'elephant'
    node2.right = node5

    node6= TreeNode()
    node6.data = 'five'
    node3.left = node6
```

```python
    #level2의 이진트리가 생성됨
    apple
    banana carrot
    donkey elephant five
```

> 내용 및 이미지 참고 : [[자료구조] 이진 트리 (Binary tree) 알아보기](https://yoongrammer.tistory.com/69), [[자료구조] 이진 트리 (Binary Tree)](https://skytitan.tistory.com/97), [5-2. [자료구조] 이진트리(binary tree)](https://kingpodo.tistory.com/27), [[자료구조] 트리(Tree)의 개념 | 이진 트리, 전 이진 트리, 완전 이진트리, 포화 이진 트리, 이진 탐색트리](https://code-lab1.tistory.com/8)

> 소스코드 참고 : [이진트리 및 완전이진트리 구현과 순회](https://seongonion.tistory.com/41), [[자료구조] 이진 트리(Binary Tree)](https://velog.io/@cha-suyeon/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%9D%B4%EC%A7%84-%ED%8A%B8%EB%A6%ACBinary-Tree)
