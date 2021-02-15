---
layout: post
title: "세그먼트 트리"
author: "Lin"
tags: 알고리즘 
---
### CS Study Day 16 - Part1

<br>

## 세그먼트 트리(Segment Tree)란?
배열에 부분 합을 구할 때 사용하는 개념입니다. 이 때 문제는 배열의 값이 지속적으로 바뀔 수 있기 때문에 매 순간 배열의 부분 길이 만큼, 즉 O(N) 만큼의 시간이 걸리기 때문에 이를 트리로 구현하여 O(logN) 의 시간으로 해결하는 방법입니다.

 

 

배열을 세그먼트 트리로 <br>
세그먼트 트리 를 사용하기 위해서는 주어진 배열을 이진 트리 구조로 만들어야 합니다. 이 때 트리를 구현하는 알고리즘은 다음과 같습니다.

1. 부모노드의 값은 양 쪽 자식 노드 값의 합
2. 배열의 요소들은 리프 노드에 위치



### 참고
https://ssungkang.tistory.com/entry/Algorithm-%EC%84%B8%EA%B7%B8%EB%A8%BC%ED%8A%B8-%ED%8A%B8%EB%A6%ACSegment-Tree
https://blog.naver.com/ndb796/221282210534