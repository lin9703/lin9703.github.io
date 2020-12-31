---
layout: post
title: "거품 정렬(Bubble Sort)"
author: "Lin"
tags: 알고리즘
---
### CS Study Day 1 - Part2

<br>
Sorting 알고리즘은 크게 Comparions 방식과 Non-Comparions 방식으로 나뉜다.

> non-Comparisons Sorting Algorithm (비교 방식 알고리즘) <br>
> - Counting Sort, Radix Sort

<br>
<hr>
<br>

## 거품 정렬(Bubble Sort)
- 데이터를 구성하는 기본 요소(Radix)를 이용하여 정렬을 진행하는 방식
- 하나의 기수마다 하나의 버킷을 생성하여, 분류를 한 뒤에, 버킷 안에서 또 정렬을 하는 방식

<br>

### JAVA 코드
{% highlight java %}
void countSort(int arr[], int n, int exp) {
	int buffer[n];
    int i, count[10] = {0};
    
    // exp의 자릿수에 해당하는 count 증가
    for (i = 0; i < n; i++){
        count[(arr[i] / exp) % 10]++;
    }
    // 누적합 구하기
    for (i = 1; i < 10; i++) {
        count[i] += count[i - 1];
    }
    // 일반적인 Counting sort 과정
    for (i = n - 1; i >= 0; i--) {
        buffer[count[(arr[i]/exp) % 10] - 1] = arr[i];
        count[(arr[i] / exp) % 10]--;
    }
    for (i = 0; i < n; i++){
        arr[i] = buffer[i];
    }
}

void radixsort(int arr[], int n) {
     // 최댓값 자리만큼 돌기
    int m = getMax(arr, n);
    
    // 최댓값을 나눴을 때, 0이 나오면 모든 숫자가 exp의 아래
    for (int exp = 1; m / exp > 0; exp *= 10) {
        countSort(arr, n, exp);
    }
}
{% endhighlight %}

<br>

### 시간 복잡도
- **O(d * (n + b))** 

<br>

### 장점
1. 문자열, 정수 정렬 가능 

<br>

### 단점
1. 자릿수가 없는 것은 정렬할 수 없음 (부동소숫점)
2. 중간 결과를 저장할 bucket 공간이 필요 








