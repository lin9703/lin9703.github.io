---
layout: post
title: "거품 정렬(Bubble Sort)"
author: "Lin"
tags: 알고리즘
---
### CS Study Day 1 - Part2

<br>
Sorting 알고리즘은 크게 Comparions 방식과 Non-Comparions 방식으로 나뉜다.

> Comparisons Sorting Algorithm (비교 방식 알고리즘) <br>
> - Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Heap Sort, Quick Sort

<br>
<hr>
<br>

## 거품 정렬(Bubble Sort)
- 서로 인접한 두 원소를 비교하여 졍렬하는 알고리즘 
- 선택 정렬과 기본 개념이 유사

<br>
### Processing
![Bubble Sort 과정](https://raw.githubusercontent.com/GimunLee/tech-refrigerator/master/Algorithm/resources/bubble-sort-001.gif)

1. 1회전에 첫 번째 원소와 두 번째 원소를, 두 번째 원소와 세 번째 원소를, 세 번째 원소와 네 번째 원소를, … 이런 식으로 (마지막-1)번째 원소와 마지막 원소를 비교하여 조건에 맞지 않는다면 서로 교환
2. 1회전을 수행하면 가장 큰 원소가 맨 뒤에 배치되니 2회전의 정렬에서 맨 뒤의 원소는 배제된다. 이런 식으로 1회전마다 제외되는 데이터가 하나씩 늘어난다.

<br>

### JAVA 코드
{% highlight java %}
public int[] bubbleSort(int[] arr) {
  for(int i = 0; i < arr.length; i++) {     // 제외될 원소의 개수를 의미 
    for(int j= 1 ; j < arr.length-i; j++) { // 원소를 비교할 index를 뽑는 반복문 
      if(arr[j-1] > arr[j]) {             // 두 원소의 대소 비교 (현재는 오름차순 정렬)
        Utils.swapValue(arr, j-1, j);
      }
    }
  }
  return arr;
}
{% endhighlight %}

<br>

### 시간 복잡도
- `(n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2` 이므로, **O(n^2)** 
- 항상 2개의 원소를 비교하기 때문에 최악의 경우, 최선의 경우, 평균의 경우 모두 시간 복잡도가 O(N^2)으로 동일

<br>

### 공간 복잡도 
- 주어진 배열 안에서 교환(swap)을 통해 정렬이 수행되므로 **O(n)**

<br>

### 장점
1. 구현이 간단하고 소스코드가 직관적
2. 제자리 정렬(in-place sorting): 정렬하고자 하는 배열 안에서 교환하는 방식으로 다른 메모리 공간을 필요하지 않는다. 
3. 안정 정렬(Stable Sort): 동일한 값에 대해 기존의 순서가 유지되는 정렬

<br>

### 단점
1. 시간 복잡도가 무조건 O(n^2)이므로 비효율적
2. 교환 연산(swap)이 많이 일어난다. (역순배열을 정렬할 때 가장 비효율적) 









