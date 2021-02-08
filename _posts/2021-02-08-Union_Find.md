---
layout: post
title: "유니온 파인드"
author: "Lin"
tags: 알고리즘 
---
### CS Study Day 15 - Part1

<br>

## Union-Find란
   Disjoint Set을 표현할 때 사용하는 알고리즘
   
- 집합을 구현하는 데는 비트 벡터, 배열, 연결 리스트를 이용할 수 있으나 그 중 가장 효율적인 트리 구조 (아래 참고*)를 이용하여 구현한다.
- 아래의 세 가지 연산을 이용하여 Disjoint Set을 표현한다.
   
   ### Union-Find의 연산
   - make-set(x)
   초기화
   x를 유일한 원소로 하는 새로운 집합을 만든다.
   - union(x, y)
   합하기
   x가 속한 집합과 y가 속한 집합을 합친다. 즉, x와 y가 속한 두 집합을 합치는 연산
   - find(x)
   찾기
   x가 속한 집합의 대표값(루트 노드 값)을 반환한다. 즉, x가 어떤 집합에 속해 있는지 찾는 연산
   https://gmlwjd9405.github.io/2018/08/31/algorithm-union-find.html

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;
import java.util.*;

public class Main {
	static int root[];
	static StringBuilder sb;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;
		sb = new StringBuilder();

        st = new StringTokenizer(br.readLine());
        int n = Integer.parseInt(st.nextToken());
        int m = Integer.parseInt(st.nextToken()); // 연산의 개수 

		root=new int[n+1];
		for (int i = 0; i < n+1; i++)
			root[i] = i;

		int s, a, b;
		for(int i=0; i<m; i++) {
			st = new StringTokenizer(br.readLine());
			s = Integer.parseInt(st.nextToken());
			a = Integer.parseInt(st.nextToken());
			b = Integer.parseInt(st.nextToken());
			if(s==0) { // 합집합
				union(a, b);
			}
			else { // 같은 집합에 포함되어 있는지 확인
				if(find(a)==find(b)) {
					sb.append("yes\n");
				}
				else {
					sb.append("no\n");
				}
			}


		}

		String text=sb.toString();
		text=text.trim();

        System.out.println(text);
    }


	/* find(x): 재귀 이용 */
	static int find(int x) {
		// 루트 노드는 부모 노드 번호로 자기 자신을 가진다.
		if (root[x] == x) {
			return x;
		} else {
			// 각 노드의 부모 노드를 찾아 올라간다.
			return root[x] = find(root[x]);
		}
	}

	/* union(x, y) */
	static void union(int x, int y){
		// 각 원소가 속한 트리의 루트 노드를 찾는다.
		x = find(x);
		y = find(y);

		root[y] = x;
	}


	
}
```



### 참고
https://gmlwjd9405.github.io/2018/08/31/algorithm-union-find.html
