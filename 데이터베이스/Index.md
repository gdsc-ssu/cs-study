# Index

## 색인(index)이란?

- 색인 : 데이터에 신속하게 접근하도록 도와주는 도구 (ex. 목차)
- 색인은 크게 정렬 색인과 해쉬 색인으로 구분할 수 있다. 
  - 정렬 색인 : 색인 레코드가 탐색키 기준으로 정렬
  - 해쉬 색인 : 탐색키를 정렬하지 않는 자료 구조

## 색인 형태

- Primary index(주 색인)

  - clustering index
  - 색인이 정렬되어 있는 순서와 동일하게 데이터 레코드를 정렬하여 데이터 파일을 저장하는 구조이다.
  - 색인은 데이터 파일 당 최대 한 개가 존재한다.

- Secondary index(이차 색인)

  <img width="398" alt="스크린샷 2022-12-24 16 41 24" src="https://user-images.githubusercontent.com/67703882/209426342-eb8eb460-7bd5-4a80-9338-8b716be6bf6b.png">

  - non-clustering index
  - 색인은 정렬되어 있지만 데이터 레코드는 정렬되지 않는 구조이다. 
  - 색인은 동일 데이터 파일에 대해 여러개가 존재할 수 있다.
  - 색인 레코드 순서와 데이터 레코드 순서가 다르기 때문에 반드시 Dense index 형태가 되어야한다.
  - Sequential scan, 즉 데이터 파일를 전체 탐색하는 연산은 이차 색인에서 굉장히 비효율적이다.

- Dense Index(밀집 색인)

  <img width="660" alt="스크린샷 2022-12-25 03 21 00" src="https://user-images.githubusercontent.com/67703882/209447391-f53028ae-82b0-4f4f-90af-e967c219b780.png" style="zoom: 50%;" >

  - **모든 탐색키 값**에 대하여 색인 레코드 혹은 엔트리가 색인에 존재하는 구조이다. 
  - 탐색키들은 파일 자체의 순서와 동일하게 유지한다. 

- Sparse Index(희소 색인)

  <img width="432" alt="스크린샷 2022-12-25 03 23 23" src="https://user-images.githubusercontent.com/67703882/209447467-7fd51ebd-d056-4640-9764-da357261f928.png">

  - **일부분의** **탐색키 값**에 대해서만 색인 엔트리가 색인에 존재하는 구조이다. 
  - 데이터가 탐색키 기준으로 무조건 정렬이 되어 있어야 한다.
  - 밀집 색인(Dense Index) 에 비해 공간은 적게 차지하지만 레코드 검색 시간이 더 걸린다.

- Multilevel index(다단계 색인)

  <img width="381" alt="스크린샷 2022-12-25 03 24 39" src="https://user-images.githubusercontent.com/67703882/209447490-24fe40b6-b1b5-4b3f-85d3-780ef2ae6da9.png">

  - 색인 파일을 대상으로 한단계 상위 색인을 또 구성하는 구조이다.
  - inner 색인(First level)와 outer 색인(Second level)로 구성되고, Third, Fourth 등 계속해서 level을 추가할 수 있다. 
  - inner 색인은 primary index 로, outer 색인은 inner 색인에 대한 sparse index 로 구성되어야한다. 

## B+ tree index

- Balanced Tree

  - Balanced Tree 는 트리의 노드가 한 방향으로 쏠리지 않도록, 노드 삽입 및 삭제시 특정 규칙에 맞게 잘 정렬되어 양쪽 자식 수의 밸런스를 유지하는 트리이다.
  - B-Tree, B* Tree, B+Tree 이 있다.
  - B-Tree 는 노드 하나에 여러 데이터가 저장될 수 있다. 각 노드 내 데이터들은 항상 정렬된 상태이고, 데이터와 데이터 사이의 범위를 이용해 자식 노드를 가진다. 

- B+ Tree

  - 루트 노드, 내부 노드(internal), 리프 노드(leaf) 로 구성된다.

  - 모든 노드에 데이터를 저장하는 B-Tree와 달리 리프 노드에만 데이터를 저장하고 내부 노드에서는 자식 포인터만 저장하는 구조이다. 리프 노드끼리는 Linked List 로 연결되어 있다. 

  - 루트에서 모든 리프 노드까지의 길이가 동일하다.

    <img width="386" alt="스크린샷 2022-12-24 16 42 00" src="https://user-images.githubusercontent.com/67703882/209426358-d1badd31-6470-4190-a7af-8885130d02af.png">

  - 루트 노드, 내부 노드(internal), 리프 노드(leaf) 로 구성된다. 
  - 루트와 내부 노드는 sparse Index 로, 리프 노드는 Dense Index 로 구성되어야 한다. 
  - 색인 노드는 탐색키 기준으로 정렬이 되어있으나. 데이터 파일은 탐색키 기준으로 정렬되어있지 않게 된다. 

- B+ tree를 사용하는 이유

  - 리프 노드를 제외한 다른 노드는 데이터를 저장하지 않기 때문에 메모리를 더 확보할 수 있다. 
  - 하나의 노드가 많은 포인터를 가질 수 있기 때문에 트리의 높이가 낮아지므로 검색 속도를 높일 수 있다. 




## 참고 자료

https://chartworld.tistory.com/18

https://velog.io/@sem/DB-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%9E%90%EB%A3%8C-%EA%B5%AC%EC%A1%B0-B-Tree