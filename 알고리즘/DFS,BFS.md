# DFS, BFS

대표적인 탐색 알고리즘인 DFS, BFS에 대해 알아보자



## DFS

DFS(Depth-First Search)는 깊이 우선 탐색 알고리즘으로, 그래프에서 깊은 부분을 우선적으로 탐색하는 알고리즘이다.

스택 자료구조 or 재귀 함수를 이용하여 알고리즘을 구현할 수 있다.

<img src="https://blog.kakaocdn.net/dn/xC9Vq/btqB8n5A25K/GyOf4iwqu8euOyhwtFuyj1/img.gif" alt="img" style="zoom:50%;" />



### 동작 과정

1. 탐색 시작 노드를 스택에 삽입하고 방문 처리를 한다.
2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면 그 인접 노드를 스택에 넣고 방문 처리를 한다. 방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼낸다.
3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.



### 시간 복잡도

: **Θ(V + E)**



### 코드

```js
// 스택
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



## BFS

BFS(Breadth-First Search)는 너비 우선 탐색 알고리즘으로, 그래프에서 가까운 노드부터 우선적으로 탐색하는 알고리즘이다.

큐 자료구조를 이용하여 알고리즘을 구현할 수 있다.

<img src="https://blog.kakaocdn.net/dn/c305k7/btqB5E2hI4r/ea7vFo08tkDYo4c8wkfVok/img.gif" alt="img" style="zoom:50%;" />



### 동작 과정

1. 탐색 시작 노드를 큐에 삽입하고 방문 처리를 한다.
2. 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리를 한다.
3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.



### 시간 복잡도

: **Θ(V + E)**



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
