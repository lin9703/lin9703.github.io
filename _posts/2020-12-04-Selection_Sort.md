---
layout: post
title: "선택 정렬(Selection Sort)"
author: "Lin"
tags: 알고리즘 CSStudy
---
### CS Study Day 2 - Part2

<br>
Sorting 알고리즘은 크게 Comparions 방식과 Non-Comparions 방식으로 나뉜다.

> Comparisons Sorting Algorithm (비교 방식 알고리즘) <br>
> - Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Heap Sort, Quick Sort

<br>
<hr>
<br>

## 선택 정렬(Selection Sort)
- 해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘 <br>
(해당 자리를 선택하고 그 자리에 오는 값을 찾는 알고리즘)
- 버블 정렬과 기본 개념이 유사

<br>
### Processing
![Selection Sort 과정](https://raw.githubusercontent.com/GimunLee/tech-refrigerator/master/Algorithm/resources/selection-sort-001.gif)

1. 배열이 오름차순이라면 최소값을 찾고 맨 앞에 위치한 값과 교환한다. (pass)
2. 1회전을 수행하면 맨 처음 위치를 뺀 나머지 배열을 같은 방법으로 교체한다. 

<br>

### JAVA 코드
{% highlight java %}
public int[] selectionSort(int[] arr) {
  int indexMin, temp;
  for(int i = 0; i < arr.length - 1; i++) {     // index 선택 
    indexMin = i;
    for(int j= i + 1; j < arr.length; j++) { // i+1번째 원소부터 선택한 index의 값과 비교
      if(arr[j] > arr[indexMin]) {             // 두 원소의 대소 비교 (현재는 오름차순 정렬)
        indexMin = j;
      }
    }
    Utils.swapValue(arr, indexMin, i);
  }
  return arr;
}
{% endhighlight %}

<br>

### 시간 복잡도
- `(n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2` 이므로, **O(n^2)** 
- 최악의 경우, 최선의 경우, 평균의 경우 모두 시간 복잡도가 O(N^2)으로 동일

<br>

### 공간 복잡도 
- 주어진 배열 안에서 교환(swap)을 통해 정렬이 수행되므로 **O(n)**

<br>

### 장점
1. 구현이 간단하고 소스코드가 직관적
2. 제자리 정렬(in-place sorting): 정렬하고자 하는 배열 안에서 교환하는 방식으로 다른 메모리 공간을 필요하지 않는다. 
3. 비교 횟수는 많지만, Bubble Sort에 비해 실제로 교환하는 횟수는 적기 때문에 교환의 리스크가 큰 자료 상태에서 비교적 효율적 

<br>

### 단점
1. 시간 복잡도가 무조건 O(n^2)이므로 비효율적
2. 불안정 정렬(Unstable Sort)









