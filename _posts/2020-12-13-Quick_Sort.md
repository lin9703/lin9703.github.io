---
layout: post
title: "퀵 정렬(Quick Sort)"
author: "Lin"
tags: 알고리즘
---
### CS Study Day 4 - Part2

<br>
Sorting 알고리즘은 크게 Comparions 방식과 Non-Comparions 방식으로 나뉜다.

> Comparisons Sorting Algorithm (비교 방식 알고리즘) <br>
> - Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Heap Sort, Quick Sort

<br>
<hr>
<br>

## 퀵 정렬(Quick Sort)
- 분할 정복 방법을 통해 주어진 배열을 정렬하는 알고리즘
    - **분할 정복(Divide and Conquer)**: 복잡한 문제를 복잡하지 않은 문제로 분할하여 정복하는 방법 
- Merge Sort와 달리 배열을 비균등하게 분할 

<br>
### Processing
1. 배열의 가운데서 하나의 원소를 고른다. 이렇게 고른 원소는 `피벗(pivot)`이라고 한다. 
2. 피벗을 기준으로 앞에는 피벗보다 작은 값들이, 뒤에는 피벗보다 큰 값들이 오도록 배열을 둘로 나눈다. (**분할(Divide)**)
3. 분할을 마친 피벗은 더 이상 움직이지 않는다. 
4. 분할된 두 개의 배열에 대해 재귀적으로 이 과정을 반복한다. <br>
-> 재귀 호출이 진행될 때마다 최소한 하나의 원소는 최종적으로 위치가 정해진다. 

- 분할(Divde): 주어진 배열을 2개의 부분 배열로 분할
- 정복(Conquer): 부분 배열을 정렬 (부분 배열의 크기가 너무 크면 순환 호출을 이용해 다시 분할 정복 방법 적용)

<br>

### JAVA 코드
{% highlight java %}
public int[] quickSort(int[] arr, int left, int right) {
  if(arr == null) return null;
  if(left >= right) return arr;
  
  int L = left;
  int R = right;
  int pivotPos = arr[(left + right) / 2]; // pivot을 배열의 가운데 위치한 요소로 결정
  
  while(L <= R) {
    while(arr[L] < pivotPos) L++; // 피벗 왼쪽에는 피벗보다 작은 원소들이 위치해야 하고 크거나 같은 원소가 있으면 반복문을 나온다.
    while(arr[R] > pivotPos) R--; // 피벗 오른쪽에는 피벗보다 큰 원소들이 위치해야 하고 작거나 같은 원소가 있으면 반복문을 나온다.
    
    if(L <= R) {
      if(L != R) {
        swap(arr, L, R); // 두 원소의 위치를 교환 -> 피벗 기준으로 왼쪽에는 작은 원소가, 오른쪽에는 큰 원소 위치
      }
      L++;
      R--;
    }
  }
  
  // 피벗의 왼쪽과 오른쪽의 정렬되지 않은 부분에 대해 퀵 정렬 수행
  if (left < R) arr = quickSort(arr, left, R);
  if (right > L) arr = quickSort(arr, L, right);
  
  return arr;
}
{% endhighlight %}

<br>

### 시간 복잡도
- 최악의 경우(pivot이 배열 내 가장 작은 값 또는 큰 값으로 설정될 때), 
매 파티션마다 `unbalanced partition`이 이뤄지고 비교 횟수는 
`(n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2` 이므로 **O(N^2)** 
- 최선의 경우(두 개의 sub-problems의 크기가 동일한 경우), **O(N logN)** <br>
-> 원소의 개수 N이 2의 거듭제곱이라고 가정할 때, N=2^3의 경우 깊이가 3이 된다. <br>
-> 이를 일반화하면 N=2^k의 경우, **k = logN** <br>
-> 각 순환 호출에서는 대부분의 레코드를 비교하므로 평균 N번 정도의 비교가 이뤄진다. <br>
-> `순환 호출의 깊이(logN) x 각 순환 호출 단계의 비교 연산(N) = N logN`
<br><br>
![시간복잡도 사진](https://raw.githubusercontent.com/GimunLee/tech-refrigerator/master/Algorithm/resources/quick-sort-002.png)

<br>

### 공간 복잡도 
- 주어진 배열 안에서 교환(swap)을 통해 정렬이 수행되므로 **O(n)**

<br>

### 장점
1. 불필요한 데이터의 이동을 줄이고 한 번 결정된 pivot은 제외되는 특성 때문에 빠른 속도 <br>
-> JAVA에서는 Arrays.sort()가 내부적으로 Dual Pivot Quick Sort로 효율적인 알고리즘 
2. 제자리 정렬(in-place sorting): 정렬하고자 하는 배열 안에서 교환하는 방식으로 다른 메모리 공간을 필요하지 않는다. 

<br>

### 단점
1. 불안정 정렬(Unstable Sort)
2. 정렬된 배열에서는 불균형 분할에 의해 오히려 많이 걸리는 수행 시간 







