# 그래프(Graph)

![](https://velog.velcdn.com/images/igun0423/post/d812a609-8a35-45f1-9ffe-9d7f2edb67e9/image.png)

그래프(Graph)는 정점(Vertex) 간선(Edge)으로 이루어진 **비선형 자료구조**이다.    
때문에 그래프(Graph)와 트리(Tree)는 정점의 관계를 표현하는 자료구조라는 점에서 동류라고 볼 수 있다.

## 용어

- `정점(vertex)`
  - `노드(node)`라고도 하며 각 정점에는 데이터가 저장된다.
- `간선(edge)`
  - `링크(arcs)`라고도 하며 각 정점간 관계를 의미한다.

# 구현 방식

## 인접행렬(Adjacency Matrix)

![](https://velog.velcdn.com/images/igun0423/post/7f3edd82-afe8-42c5-8d68-9dc881d3c274/image.png)

2차원 배열에 각 정점이 연결된 형태를 표현하는 방식이다.

### 장점

1. 구현이 빠르다.
2. 검색 속도가 O(1)로, 빠르다.

### 단점

1. 생성 시 O(n^2)의 시간 복잡도를 갖는다.
2. 무조건 2차원 배열 이상의 공간이 필요하기에, 공간 낭비가 심하다.

## 인접리스트(Adjacency List)

![](https://velog.velcdn.com/images/igun0423/post/d73629be-8b5d-4233-82e8-16367602ef3a/image.png)

모든 정점에 연결된 정점들을 리스트로 표현하는 방식이다.

### 장점

1. 검색 속도가 O(n)으로, 빠른 편이다.
2. 필요한 만큼만 공간을 사용하기 때문에, 공간 낭비가 적다.

### 단점

1. 검색 속도가 `인접행렬(Adjacency Matrix)`에 비해 느리다.
2. 구현이 비교적 어렵다.

# 그래프(Graph)의 종류

## 무방향 그래프 (Undirected Graph)

![](https://velog.velcdn.com/images/igun0423/post/954ab6ef-bf08-4bd8-b853-7addc05c0555/image.png)

정점을 연결하는 간선에 방향이 없는 그래프를 말한다.

## 방향 그래프 (Directed Graph)

![](https://velog.velcdn.com/images/igun0423/post/52811c82-43bb-427e-a488-101b4c684262/image.png)

정점을 연결하는 간선에 방향이 있는 그래프를 말한다.
간선의 방향대로만 이동할 수 있다.

## 가중치 그래프 (Weighted Graph)

![](https://velog.velcdn.com/images/igun0423/post/be924a8e-ff2f-4f14-b142-4e3acc3999f7/image.png)

두 정점을 이동하는 비용이 존재하는 그래프를 말한다.

## 완전 그래프 (Completed Graph)

![](https://velog.velcdn.com/images/igun0423/post/52513804-b5c4-4fd4-9e8a-9e7b44af55a7/image.png)

모든 정점이 연결되어있는 그래프를 말한다.

# 그래프(Graph)의 탐색

> 그래프의 모든 정점을 한 번씩 방문하는 것을 `탐색`이라고 한다.

![](https://velog.velcdn.com/images/igun0423/post/9ec35b35-a98e-4bdb-bb95-2774f5bc2061/image.gif)

DFS와 BFS 관련된 자세한 내용은 추후 알고리즘 파트에서 다루도록 한다.

## 깊이 우선 탐색(Depth-First Search)

그래프의 가장 깊은 곳 까지 내려간 후, 더 이상 내려갈 정점이 없으면 옆으로 이동하는 탐색 기법

- 재귀 호출
- `스택(Stack)`

## 너비 우선 탐색(Breadth-First Search)

그래프에서 최대한 넓게 이동한 후, 더 이상 이동할 정점이 없으면 내려가는 탐색 기법

- `큐(Queue)`

# 자바스크립트와 그래프(Graph)

```javascript
class Graph {
  constructor() {
    //기본 생성자
    this.nodes = {};
  }

  addNode(node) {
    //노드 추가
    this.nodes[node] = this.nodes[node] || [];
  }

  contains(node) {
    //그래프에 해당 노드가 존재하는지 여부
    let result = null;
    this.nodes[node] ? (result = true) : (result = false);
    return result;
  }

  removeNode(node) {
    //노드 삭제
    this.nodes[node] ? delete this.nodes[node] : this.nodes[node];
  }

  hasEdge(fromNode, toNode) {
    //두 노드 사이 간선의 존재 여부
    let result = null;
    this.nodes[fromNode] &&
    this.nodes[toNode] &&
    this.nodes[fromNode].includes(toNode) &&
    this.nodes[toNode].includes(fromNode)
      ? (result = true)
      : (result = false);
    return result;
  }

  addEdge(fromNode, toNode) {
    //두 노드 사이에 간선 추가
    this.nodes[fromNode].push(toNode);
    this.nodes[toNode].push(fromNode);
  }

  removeEdge(fromNode, toNode) {
    //두 노드 사이 간선을 삭제
    let node = this.nodes[fromNode];
    if (
      this.nodes[fromNode].includes(toNode) &&
      this.nodes[toNode].includes(fromNode)
    ) {
      this.nodes[fromNode][node.indexOf(toNode)] = "";
      this.nodes[toNode][node.indexOf(fromNode)] = "";
    }
  }
}

const graph = new Graph();
graph.addNode(100);
graph.addNode(1);
graph.addNode(200);
graph.addNode(400);
graph.addEdge(100, 400);
graph.addEdge(400, 200);
console.log(graph);

/**
Graph {
  nodes: { '1': [], '100': [ 400 ], '200': [ 400 ], '400': [ 100, 200 ] }     
}
*/
```

# Reference

- [비선형 자료구조 - 그래프(Graph)](https://velog.io/@codenmh0822/%EB%B9%84%EC%84%A0%ED%98%95-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%9E%98%ED%94%84Graph)
- [[Algorithm] 자료구조 그래프(Graph)란 무엇인가?](https://coding-factory.tistory.com/610)
- [[11] [알고리즘 - 자료구조] 그래프(graph)란? (비선형구조) javascript 구현](https://developerjun2.tistory.com/148)
- [[Data Structure] 자바스크립트로 그래프 Graph 구현하기](https://velog.io/@nomadhash/Data-Structure-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A1%9C-%EA%B7%B8%EB%9E%98%ED%94%84-Graph-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0#graph%F0%9F%A4%B7%E2%99%82%EF%B8%8F)
