# DFS, BFS

대표적인 탐색 알고리즘들인 DFS, BFS에 대해 알아보자

<br>

## DFS

DFS(Depth-First Search)는 깊이 우선 탐색 알고리즘으로, 그래프에서 깊은 부분을 우선적으로 탐색하는 알고리즘이다.

스택 자료구조 or 재귀 함수를 이용하여 알고리즘을 구현할 수 있다.

<img src="https://blog.kakaocdn.net/dn/xC9Vq/btqB8n5A25K/GyOf4iwqu8euOyhwtFuyj1/img.gif" alt="img" style="zoom:50%;" />

<br>

### 동작 과정

1. **스택을 사용한 방식**	

   1. 탐색 시작 노드를 스택에 삽입하고 방문 처리를 한다.

   2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면 그 인접 노드를 스택에 넣고 방문 처리를 한다. 방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼낸다.

   3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.

2. **재귀를 이용한 방식**
   1. 현재 노드를 방문 처리
   2. 현재 노드와 연결된 다른 노드를 재귀적으로 방문

<br>

### 시간 복잡도

: **Θ(V + E)**

<br>

### 코드

```js
// 재귀 함수
const dfs = (graph, node, visited) => {
  visited[node] = true;
 	answer.push(node);
  
  graph[node].forEach((nextNode) => {
    if(!visited[nextNode]) {
      dfs(graph, nextNode, visited);
    }
  });
}
```

<br>

## BFS

BFS(Breadth-First Search)는 너비 우선 탐색 알고리즘으로, 그래프에서 가까운 노드부터 우선적으로 탐색하는 알고리즘이다.

큐 자료구조를 이용하여 알고리즘을 구현할 수 있다.

<img src="https://blog.kakaocdn.net/dn/c305k7/btqB5E2hI4r/ea7vFo08tkDYo4c8wkfVok/img.gif" alt="img" style="zoom:50%;" />

<br>

### 동작 과정

1. 탐색 시작 노드를 큐에 삽입하고 방문 처리를 한다.
2. 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리를 한다.
3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.

<br>

### 시간 복잡도

: **Θ(V + E)**

<br>

### 코드

```js
const bfs = (graph, startNode) => {
  const visited = []; // 탐색을 마친 노드들
  const queue = []; // 탐색해야할 노드들

  queue.push(startNode);

  while (queue.length !== 0) { 
    const node = queue.shift();
    
    if (!visited.includes(node)) {
      visited.push(node); 
      queue = [...queue, ...graph[node]];
    }
  }
  
  return visited;
};
```

