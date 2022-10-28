# 연결리스트 (Linked List)
> 연결 리스트 : 고정 크기의 배열 등에 의해 구현된 선형 리스트의 단점을 보완한 자료구조

## ✅ 연결 리스트(Linked List)란?
- 각 노드가 **데이터와 포인터**를 가지고 한 줄로 연결되어있는 방식으로 데이터를 저장하는 자료구조
- 각 노드는 **다음 노드를 가리키는 포인터** 포함
    - 다음 노드를 가리키는 포인터 : **다음 노드의 주소**를 값으로 가짐
<img width="706" alt="스크린샷 2022-10-28 오후 12 37 56" src="https://user-images.githubusercontent.com/66112716/198498261-a200a69c-7247-4a61-aa33-6345a7d48f21.png">
<img width="702" alt="스크린샷 2022-10-28 오후 12 38 17" src="https://user-images.githubusercontent.com/66112716/198498278-bda2dda6-9d69-48e4-b0a0-36b8693c0dee.png">

- `{ node : (data, link) }`
- 데이터 및 링크(포인터)에 의해 비연속적으로 연결된 선형 자료구조

## ✅ 배열 vs 연결 리스트
- **배열** :
    1. **연속적인 공간 할당**을 통해 메모리 저장
    2. `index`를 통해 원소 접근 - 데이터 주소의 식별자
    3. 특정 원소의 접근 용이
    4. 원소의 삽입/삭제 비용 ↑ & 추가 작업 필요 (원소 위치 조정)

- **리스트** :
    1. **비연속적인 공간 할당**을 통해 메모리 저장(비연속적으로 할당될 수 있기에 데이터의 주소 계산이 어려울 수 있음)
    2. `link`를 통해 원소 접근 - 데이터의 순서 식별자
    3. 특정 원소로의 직접적인 접근 불가능 → 원소 검색 어려움
    4. 원소의 삽입/삭제 비용 ↓ → 동적인 노드의 삽입 삭제 (추가 작업 필요 X)

## ✅ 연결 리스트의 특징
- **포인터**로 연결됨
    - 메모리 내 어느 위치에나 원소 존재 가능
    - **동적**으로 원소의 삽입/삭제가 이루어짐
        - 원소의 삽입 삭제 시 **데이터의 이동**을 비롯한 추가 작업이 필요 없음 
        - cf) 배열
    - 원소의 끝 포인터는 `null`을 지시하여 리스트의 끝을 알림

- **가변적인** 메모리의 크기
    - 메모리를 허용하는 만큼 크기가 커질 수 있음
    - **효율적인 메모리 공간** 사용
        → **포인터**를 위한 **추가 메모리**가 필요함    

- 원소의 순서 유지 및 접근
    - 원소의 순서 : 노드의 **링크**를 이용해 유지
    - 원소로의 접근 : 순차적으로 줄을 따라 접근
        - **검색**의 시간 복잡도 측면에서는 단점
            - worst case : `O(n)` 소요

- 구현 난이도 ↑ 
    - cf) 선형 리스트
    - 포인터의 저장이 필요하므로 저장 공간이 추가적으로 요구됨

- 타 자료구조(ex. 추상자료형, ADT ...)의 기반
    - ex) queue, stack, hash table ...

## ✅ 연결 리스트의 노드
- 리스트의 첫 노드 : `Head`노드
- 리스트의 끝 노드 : `Tail`노드, `End`노드

## ✅ 연결 리스트 구현
### 1. Node 클래스 선언 및 초기화
- 각 노드는 데이터를 저장하는 `data`와 다음 노드로의 연결을 위한 `next` 포인터를 멤버 변수로 가짐
```py
class Node:
    def __init__(self, data, next):
        self.data = data  # 데이터
        self.next = next  # 링크(포인터)
```

### 2. LinkedList 클래스 선언 및 초기화
- `LinkedList` 클래스에서는 링크드리스트의 노드 개수를 가리키는 `no`, 첫 노드인 `head`, 현재 노드인 `current` 멤버변수를 가짐
- `__len__` 메소드를 통해 링크드리스트의 노드 개수, 즉 길이를 반환하는 기능 구현
```py
class LinkedList:
    def __init__(self):
        self.no = 0          # 링크드리스트 노드 개수
        self.head = None     # 머리 노드
        self.current = None  # 주목 노드

    def __len__(self):
        return self.no # 링크드리스트 노드 개수 반환
```

### 3. 검색(`search`) 메소드, 포함 여부 확인(`__contains__`) 메소드 구현
- `search` 메소드
    - 포인터 변수(`ptr`)의 값을 `head` ~ `tail`으로 선형탐색
    - 메소드의 파라미터로 전달받은 `data`와 일치하는 노드를 발견하였을 때 해당 노드의 위치인 `cnt`를 반환

- `__contains__` 메소드
    - `search` 메소드 실행을 통해 파라미터로 전달받은 `data`의 포함 여부를 확인
```py
def search(self, data):
    # data와 값이 같은 노드를 검색
    cnt = 0
    ptr = self.head
    while ptr is not None:
        if ptr.data == data:
            self.current = ptr
            return cnt
        cnt += 1
        ptr = ptr.next
    return -1
def __contains__(self, data):
    # 링크드리스트의 data 포함 여부를 확인
    return self.search(data) >= 0
```

### 4. 노드 추가 함수(`add_first` & `add_last`) 구현
- `add_first` : 링크드리스트의 앞에 노드를 추가하는 메소드
    1. `head`를 새로운 노드로 교체
    2. 이전 `head`가 가리키던 노드를 새로운 노드의 다음 노드로 연결

- `add_last` : 링크드리스트의 뒤에 노드를 추가하는 메소드
    1. `head`의 empty 여부
        - head가 비어있음 : 리스트의 맨 앞에 노드 삽입(`add_first`)
        - head가 비어있지 않음 : `tail`노드로 이동해 tail노드의 다음 노드에 새로운 노드 추가
```py
# 맨 앞에 노드 삽입
def add_first(self, data):
    ptr = self.head  # 삽입 전의 머리 노드
    self.head = self.current = Node(data, ptr)
    self.no += 1

# 맨 뒤에 노드 삽입
def add_last(self, data):
    if self.head is None :    # 리스트가 비어 있으면
        self.add_first(data)  # 맨앞에 노드 삽입
    else:
        ptr = self.head
        while ptr.next is not None:
            ptr = ptr.next  # while문을 종료할 때 ptr은 꼬리 노드를 참조
        ptr.next = self.current = Node(data, None)
        self.no += 1
```

### 5. 노드 삭제 함수(`remove_first` & `remove_last`) 구현
```py
# 맨 앞 노드(head) 삭제
def remove_first(self):
    if self.head is not None:  # 리스트가 비어 있으면
        self.head = self.current = self.head.next
    self.no -= 1

# 맨 뒤 노드(tail) 삭제
def remove_last(self):
    if self.head is not None:
        if self.head.next is None :  # 노드가 1개 뿐이라면
            self.remove_first()      # 머리 노드를 삭제
        else:
            ptr = self.head  # 스캔 중인 노드
            pre = self.head  # 스캔 중인 노드의 앞쪽 노드
            while ptr.next is not None:
                pre = ptr
                ptr = ptr.next # while문 종료시 ptr은 꼬리 노드를 참조하고 pre는 맨끝에서 두 번째 노드를 참조
            pre.next = None  # pre는 삭제 뒤 꼬리 노드
            self.current = pre
            self.no -= 1
```

### 6. 입력받은 파라미터와 일치하는 노드 삭제 함수(`remove`) 구현
- `remove` 메소드 
    - 파라미터 `p`를 `head`노드부터 선형 탐색해 일치하는 노드를 삭제
```py
def remove(self, p):
    if self.head is not None:
        if p is self.head:       # p가 머리 ​​노드이면
            self.remove_first()  # 머리 노드를 삭제
        else:
            ptr = self.head
            while ptr.next is not p:
                ptr = ptr.next
                if ptr is None:
                    return  # ptr은 리스트에 존재하지 않음
            ptr.next = p.next
            self.current = ptr
            self.no -= 1
```

## ✅ 연결 리스트 종류
### 단순 연결 리스트 (Singly Linked List)
<img src="https://user-images.githubusercontent.com/66112716/198505061-308579db-1449-421a-82c5-6fc45881de31.jpeg" width="70%" />

- 노드를 한 줄로 연결시킨 자료구조
- 각 노드마다 `값(데이터) : 링크(포인터)`를 가짐
- 단방향 연결 : 각 원소 별 단방향 단일 링크(포인터) 필드가 필요함
- `데이터 | 링크` → `다음 노드` → `다음 노드` → ...
- 마지막 노드의 링크 : `null`값을 가짐

### 이중 연결 리스트 (Doubly Linked List)
<img src="https://user-images.githubusercontent.com/66112716/198505109-b578b0c9-549d-4f23-bdfe-207f7fd36014.jpeg" width="70%" />

- **양방향** 연결 : 후행 노드와 선행 노드 모두를 가리킴
- 각 노드별로 **2개의 링크(포인터)**를 가짐
- `{ node : (prev link, data, next link) }`
- 순방향 & 양방향 탐색 가능

### 원형 연결 리스트 (Circular Linked List)
<img src="https://user-images.githubusercontent.com/66112716/198505080-e7c25d0d-1d4b-47aa-8669-8476910ce1ac.jpeg" width="70%" />

- 마지막 노드의 링크가 **리스트의 첫번째 노드**를 가리킴
- 단순 연결 리스트의 마지막 노드 줄을 첫 노드와 연결한 형태

### 청크 리스트 (Chunked List)
- 배열과 리스트의 장점을 합친 형태
- 리스트의 멤버를 **레코드의 배열**로 지정
    - CPU의 cache 기능이 있는 경우 지역성(locality)이 떨어지는 연결리스트의 성능 문제를 보완

> 소스코드 참고 : [Do it! 자료구조와 함께 배우는 알고리즘 입문](https://search.shopping.naver.com/book/catalog/32485046073) 

> [사진 | 자료 출처 1](https://code-lab1.tistory.com/2)

> [자료 출처 2](http://www.ktword.co.kr/test/view/view.php?m_temp1=3559)