---
layout: post
title: "삽입 정렬(Insertion Sort)"
author: "Lin"
tags: 알고리즘
---
### CS Study Day 3 - Part2

<br>
Sorting 알고리즘은 크게 Comparions 방식과 Non-Comparions 방식으로 나뉜다.

> Comparisons Sorting Algorithm (비교 방식 알고리즘) <br>
> - Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Heap Sort, Quick Sort

<br>
<hr>
<br>

## 삽입 정렬(Insertion Sort)
- 손 안의 카드를 정렬하는 방법과 유사 <br>
(새로운 카드를 기존의 정렬된 카드 사이의 올바른 자리를 찾아 삽입)
- 2번째 원소부터 시작하여 그 앞의 원소들과 비교하여 삽입할 위치를 지정한 후, 지정된 자리에 자료를 삽입하는 알고리즘 
- 선택 정렬과 유사하지만 더 효율적 

<br>
### Processing
![Insertion Sort 과정](https://raw.githubusercontent.com/GimunLee/tech-refrigerator/master/Algorithm/resources/insertion-sort-001.gif)

1. 2번째 index의 값을 temp에 저장
2. temp와 이전에 있는 원소들을 비교하며 삽입 
3. 다음 index의 값을 temp에 저장해 1-2번 반복 

<br>

### JAVA 코드
{% highlight java %}
public int[] insertionSort(int[] arr) {
  for(int i = 1; i < arr.length; i++) { // 첫 번째 원소는 앞에 어떤 원소도 갖고 있지 않기 때문에 두 번째부터 시작 
    int temp = arr[i];
    int prev = index - 1;    
    while((prev >= 0) && (arr[prev] > temp)) { // temp가 prev보다 작을 때 오른쪽으로 한 칸씩 이동 
      arr[prev+1] = arr[prev];
      prev--;
    }
    arr[prev+1] = temp; // prev는 temp보다 작은 값들 중 제일 큰 값의 위치 가르킴
  }
  return arr;
}
{% endhighlight %}

<br>

### 시간 복잡도
- 최악의 경우(역정렬), 선택 정렬과 마찬가지로 `(n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2` 이므로, **O(n^2)** 
- 최선의 경우(모두 정렬), 한번씩 밖에 비교를 하지 않으므로 **O(n)** 
- 이미 정렬되어 있는 배열에 자료를 하나씩 삽입/제거하는 경우에는 현실적으로 최고의 정렬 알고리즘 (탐색을 제외환 오버헤드가 적기 때문에)

<br>

### 공간 복잡도 
- 주어진 배열 안에서 교환(swap)을 통해 정렬이 수행되므로 **O(n)**

<br>

### 장점
1. 대부분의 원소가 이미 정렬되어 있는 경우 매우 효율적 
2. 제자리 정렬(in-place sorting): 정렬하고자 하는 배열 안에서 교환하는 방식으로 다른 메모리 공간을 필요하지 않는다. 
3. 안정 정렬(Stable Sort): 동일한 값에 대해 기존의 순서가 유지되는 정렬
4. 버블 정렬이나 선택 정렬과 같은 O(n^2) 알고리즘에 비교하여 상대적으로 빠르다.

<br>

### 단점
1. 평균과 최악의 시간 복잡도가 O(n^2)이므로 비효율적
2. 버블 정렬과 선택 정렬과 마찬가지로, 배열의 길이가 길어질수록 비효율적 








