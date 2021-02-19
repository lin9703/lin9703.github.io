---
layout: post
title: "Prim Algorithm"
author: "Lin"
tags: 알고리즘  
---
### CS Study Day 17 - Part2

<br>

## Prim Algorithm
시작 정점에서부터 출발하여 신장트리 집합을 단계적으로 확장해나가는 방법
- 정점 탐색 기반
- Greedy 기법
- 각 정점의 가중치를 비교하기 때문에 정점의 수가 적을수록 유리 <br>
(정점보다 간선의 수가 많은 Dense Graph에서 유리)

> - spanning tree: 그래프 G의 모든 vertex가 cycle 없이 연결된 형태
> - Minimum Spanning Tree(MST): 그래프 G 의 spanning tree 중 edge weight 의 합이 최소인 spanning tree

<br>

#### 동작
1. 시작 단계에서는 시작 정점만이 MST(최소 비용 신장 트리) 집합에 포함된다. 
2. 앞 단계에서 만들어진 MST 집합에 인접한 정점들 중에서 최소 간선으로 연결된 정점을 선택하여 트리를 확장한다.
즉, 가장 낮은 가중치를 먼저 선택한다.
3. 위의 과정을 트리가 (N-1)개의 간선을 가질 때까지 반복한다.



<br>
[출처]
https://gmlwjd9405.github.io/2018/08/30/algorithm-prim-mst.html
https://velog.io/@agugu95/Prims-Algorithm%ED%94%84%EB%A6%BC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98