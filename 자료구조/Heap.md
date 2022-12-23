# Heap

힙은 우선순위 큐를 구현하는 대표적인 수단이다. 힙에 대해 알아보기 전에 우선순위 큐가 무엇인지 알아보자.

<br>

## Priority Queue (우선순위 큐)

기존의 Queue(큐)는 먼저 들어온 데이터가 먼저 나가는 FIFO 방식의 자료구조이다. 하지만 Priority Queue(우선순위 큐)는 들어온 순서가 아닌, **우선순위가 높은** 데이터가 먼저 나가는 방식의 자료구조이다.

우선순위 큐는 선형적인 방식으로도 구현이 가능하지만, 이는 비효율적이다. 예를 들어, 연결 리스트, 배열, 스택, 큐 등으로 우선순위 큐를 구현할 경우, 우선순위가 가장 높은 데이터를 찾기 위해 모든 데이터를 확인해야하므로 탐색의 시간복잡도가 O(n)이다.

그래서 우선순위 큐를 구현할 때 우선순위가 가장 높은 데이터를 최상단에 놓는 **완전 이진 트리**를 사용하는 **힙** 자료구조가 대표적으로 사용된다.

<br>

## Heap (힙)

- **완전 이진 트리** 자료 구조를 기반으로 하는 자료구조이다.
  
  - 완전 이진 트리가 아닌 경우, 선형 방식과 동일한 성능이 나온다.
  
- **1차원 배열**로 나타낼 수 있다.
  - `A[k]` 노드의 자식 노드는 `A[2k+1]`, `A[2k+2]`
  - `A[k]` 노드의 부모 노드는 `A[(k-1)/2]` (내림)

- 힙 특성

  - Max Heap(최대 힙): 부모 노드의 값이 자식 노드의 값보다 크거나 같은 완전 이진 트리
  
  
    - Min Heap(최소 힙): 부모 노드의 값이 자식 노드의 값보다 작거나 같은 완전 이진 트리
  

<img src="https://user-images.githubusercontent.com/70627979/148479250-aa3d6da2-c0ba-48de-be15-acdbc0bc1dc5.png" alt="image" style="zoom:25%;" />

<br>

## 힙 구현

힙은 일반적으로 배열을 이용해 구현한다. 아래는 최대 힙의 삽입, 삭제 동작 방식과 임의의 배열을 힙으로 구성하는 방식에 대한 설명이다.

- 힙의 **삽입, 삭제 시간복잡도**는 `O(log(n))`이다.

<br>

### 삽입

1. 삽입할 노드를 **맨 끝에 추가** (완전 이진 트리 유지)

2. 현재 노드와 부모 노드를 비교하여 **현재 노드가 더 클 경우** 부모 노드와 **교체** (반복)

3. 부모 노드의 값이 더 작거나 같으면 종료

<br>

### 삭제

우선순위가 가장 높은 루트 노드가 삭제 대상이다.

1. 맨 마지막 노드를 루트 노드로 이동
2. 현재 노드를 자식 노드들과 비교하여 값이 가장 큰 노드와 변경 (반복)
3. 리프노드로 이동하거나, 모든 자식 노드보다 크면 종료

<br>

### 힙 생성

임의의 배열을 받아 힙으로 구성하는 방식이다.

- 모든 서브 트리가 힙의 성질을 만족하도록 노드 교환하고, 두 개의 서브 트리(힙)를 병합하여 하나의 큰 힙으로 구성
- 최종적으로 하나의 힙을 완성 (재귀 방식)

<br>

절차

1. 자식 노드 중 큰 값을 가진 것과 교환
2. 모든 자식 노드보다 크거나 같은 값을 가지면 종료
3. `A[(n-1)-1 // 2]` 부터 `A[0]` 까지 1,2번 반복

<br>

### 코드

- 파이썬 버전

  ```python
  class Heap:
    def __init__(self, *args):
      if len(args) != 0:
        self.__A = args[0]  # 파라미터로 온 리스트
      else:
        self.__A = []
  
    # 삽입 (재귀 알고리즘 버전)
    def insert(self, x):
      self.__A.append(x)
      self.__percolateUp(len(self.__A) - 1)
  
    def __percolateUp(self, i:int):
      parent = (i - 1) // 2
      if i > 0 and self.__A[i] > self.__A[parent]:
        self.__A[i], self.__A[parent] = self.__A[parent], self.__A[i]
        self.__percolateUp(parent)
  
    # 삭제 (재귀 알고리즘 버전)
    def deleteMax(self):
      if (not self.isEmpty()):
        max = self.__A[0]
        self.__A[0] = self.__A.pop()
        self.__percolateDown(0)
        return max
      else:
        return None
  
    def __percolateDown(self, i:int):
      child = 2 * i + 1
      right = 2 * i + 2
      
      if (child <= len(self.__A)-1):
        if (right <= len(self.__A)-1 and self.__A[child] < self.__A[right]):
            child = right  # 더 큰 값과 교환
  
        if self.__A[i] < self.__A[child]:
          self.__A[i], self.__A[child] = self.__A[child], self.__A[i]
          self.__percolateDown(child)
  
    # 힙 생성
    def buildHeap(self):
      for i in range((len(self.__A) - 2) // 2, -1, -1):
        self.__percolateDown(i)
  
    # 최대 힙의 최댓값 확인
    def max(self):
      return self.__A[0]
  
    # 힙 비었는지 확인
    def isEmpty(self) -> bool:
      return len(self.__A) == 0
  
    # 힙 초기화
    def clear(self):
      self.__A = []
  
    # 힙 크기
    def size(self) -> int:
      return len(self.__A)
  
    # 힙 출력
    def heapPrint(self):
      print('========')
  
      idx = 0
      printLen = 1
  
      while(idx < self.size()):
        for l in range(0, printLen):
          if (idx < self.size()):
            print(self.__A[idx], end=' ')
          idx += 1
        printLen *= 2
        print('')    
      
      print('========')
  ```

<br>

## 참고 자료

- https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/DataStructure#binary-heap
- https://www.youtube.com/watch?v=jfwjyJvbbBI&list=PLjSkJdbr_gFY8VgactUs6_Jc9Ke8cPzZP&index=3