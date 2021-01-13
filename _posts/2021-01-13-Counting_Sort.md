---
layout: post
title: "계수 정렬(Counting Sort)"
author: "Lin"
tags: 알고리즘
---
### CS Study Day 8 - Part2

<br>
Sorting 알고리즘은 크게 Comparions 방식과 Non-Comparions 방식으로 나뉜다.

> non-Comparisons Sorting Algorithm (비교 방식 알고리즘) <br>
> - Counting Sort, Radix Sort

<br>
<hr>
<br>

## 계수 정렬(Counting Sort)
- 몇 개인지 개수를 세어 정렬하는 방식
- 조건을 만족해야만 적용 가능
```
1. 배열의 모든 원소는 정수
2. 배열의 모든 원소의 범위는 0~k (k는 정수)
3. k=O(n)으로 나타낼 수 있어야 한다.
```

<br>

<br>
### Processing
1. 정렬하고자 하는 값 중 최댓값에 해당하는 값을 size로 하는 임시 배열을 만든다.
2. 임시 배열의 index에 해당하는 값이 몇 개인지 추가한다.
3. 임시 배열의 값을 누적값으로 바꾼다. 
    - 맨 마지막 원소는 당연하게도 원래 배열의 길이가 된다.
    - 임시 배열의 index는 정렬하고자 하는 값, value는 그 값들이 정렬되었을 때의 index를 나타낸다. 
4. 임시 배열을 활용하여 뒤에서부터 정렬 

<br>

### JAVA 코드
{% highlight java %}
int arr[5];  // [5, 4, 3, 2, 1]
int sorted_arr[5];
// 과정 1 - counting 배열의 사이즈를 최댓값이 담기도록 크게 잡기
int counting[6];	// 단점 : counting 배열의 사이즈의 범위를 가능한 값의 범위만큼 크게 잡아야 하므로이 비효율적

// 과정 2 - counting 배열의 값을 증가 
for (int i = 0; i < arr.length; i++) {
    counting[arr[i]]++;
}

// 과정 3 - counting 배열을 누적합으로 만들기 
for (int i = 1; i < arr.length; i++) {
    counting[i] += counting[i - 1];
}
// 과정 4 - 뒤에서부터 배열을 돌면서 해당하는 값의 인덱스에 값 넣기
for (int i = arr.length - 1; i >= 0; i--) {
    sorted_arr[counting[arr[i]]] = arr[i];
    counting[arr[i]]--;
}
{% endhighlight %}

<br>

### 시간 복잡도
- 과정 2: O(n), 과정 3: O(k), 과정 4: O(n) (k는 원소의 최댓값, n은 원소의 개수) 
- 다 더해서 **O(n+k)**
- 만약 k=O(n)이면 **O(n)**

<br>

### 공간 복잡도 
- 최댓값만큼 배열을 만들어야 해서 **O(k)**

<br>

### 장점
1. 비교를 하지 않기 때문에 빠른 시간복잡도 
2. 안정 정렬(Stable Sort): 동일한 값에 대해 기존의 순서가 유지되는 정렬

<br>

### 단점
1. 최댓값이 너무 커지면 느려지고 메모리 낭비가 심각
2. 제자리 정렬이 아님 







