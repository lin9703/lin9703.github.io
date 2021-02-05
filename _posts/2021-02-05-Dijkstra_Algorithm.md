---
layout: post
title: "LCA(Lowest Common Ancestor"
author: "Lin"
tags: 알고리즘
---
### CS Study Day 14 - Part1

<br>

## 다익스트라 알고리즘

다익스트라 알고리즘(Dijkstra’s algorithm)은 최단 경로(Shortest Path)를 찾는 대표적인 기법 가운데 하나이다.

하나의 시작 정점으로부터 모든 다른 정점까지의 최단 경로를 찾는 알고리즘이다.

다익스트라 알고리즘은 너비우선탐색(BFS)을 기본으로 한다.

음수 가중치가 포함되어 있다면 사용할 수 없다.

경로 탐색을 위한 알고리즘(DFS,BFS)는 가중치가 있을 때 최단 거리를 표현하기가 어렵다.

<br>

###동작 과정

Dijkstra의 알고리즘에서는 시작 정점에서 다른 정점으로 가는 최단 거리를 기록하는 배열이 반드시 있어야 한다.

단, 정점 v에서 정점 w로의 직접 간선이 없을 경우에는 무한대의 값을 저장한다.

알고리즘이 진행되면서 최단 거리가 발견되는 정점들이 집합 S에 하나씩 추가될 것이다.

알고리즘의 매 단계에서 집합 S 안에 있지 않은 정점 중에서 가장 Distance 값이 작은 정점을 S에 추가한다.


[참고]
https://goodgid.github.io/Dijkstra-Algorithm/