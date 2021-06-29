---
layout: single
title: "Graph Search"
categories:
    - Python
tags:
    - Python
    - Algorithms
    - Problem Solving
---

# BFS

<p align="center">![BFS](https://upload.wikimedia.org/wikipedia/commons/5/5d/Breadth-First-Search-Algorithm.gif)</p>

- 너비 우선 탐색이라 하며 **BFS(Breadth-First Search)**라 부른다.
- 루트 노드 혹은 임의의 노드에서 시작해 인접한 노드를 먼저 탐색하는 방법이다.
- 시작 정점으로부터 가까운 정점을 먼저 방문하고 멀리 떨어져 있는 정점을 나중에 방문하는 순회 방법이다.
- 즉, 깊게 탐색하기 전에 넓게 탐색하는 것이다.
- 정점의 수를 $V$, 간선의 수를 $E$라 하면, 인접행렬에 대한 BFS의 시간복잡도는 $$O(V^2)$$이고, 인접리스트에 대한 BFS의 시간복잡도는 $$O(V + E)$$이다.

## Idea

큐를 이용하면 구현할 수 있다.

## Code

``` python
from collections import deque


graph = {1: [2, 3, 4],
         2: [5],
         3: [6, 7],
         4: [8],
         5: [9],
         6: [10],
         7: [],
         8: [],
         9: [],
         10: []}


def bfs(root):
    queue = deque()
    queue.append(root)

    while queue:
        node = queue.popleft()
        print(node)  # visit
        queue.extend(graph[node])


bfs(1)
```

## When?

최소 비용의 케이스를 탐색하는 것이 하나의 완전한 경로를 탐색하는 것보다 중요할 때, BFS가 유용할 수 있다.



# DFS

<p align="center">![DFS](https://upload.wikimedia.org/wikipedia/commons/7/7f/Depth-First-Search.gif)</p>

- 깊이 우선 탐색이며 **DFS(Depth-First Search)**라고 부른다.
- 루트 노드에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색한다.
- 넓게 탐색하기 전에 깊게 탐색하는 것이다.
- 예를 들어, 미로를 탐색할 때 한 방향으로 갈 수 있을 때까지 계속 가다가 더 이상 갈 수 없게 되면 다시 가장 가까운 갈림길로 돌아와서 이곳으로부터 다른 방향으로 다시 탐색을 진행하는 방법과 유사하다.
- 정점의 수를 $V$, 간선의 수를 $E$라 하면, 인접행렬에 대한 DFS의 시간복잡도는 $$O(V^2)$$이고, 인접리스트에 대한 DFS의 시간복잡도는 $$O(V + E)$$이다.

## Idea

스택 또는 재귀를 이용하면 구현할 수 있다.

## Code

``` python
graph = {1: [2, 5, 9],
         2: [3],
         3: [4],
         4: [],
         5: [6, 8],
         6: [7],
         7: [],
         8: [],
         9: [10],
         10: []}


def dfs(root):
    stack = list()
    stack.append(root)

    while stack:
        node = stack.pop()
        print(node)  # visit
        stack.extend(graph[node])


dfs(1)
```

## When?

일단 완전한 하나의 경로를 찾는 것이 우선일 경우, DFS가 유용할 수 있다.
