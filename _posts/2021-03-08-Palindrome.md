---
layout: post
title: "Palindrome(회문) 알고리즘"
author: "Lin"
tags: 알고리즘 
---
### CS Study Day 21 - Part3

<br>

## Palindrome(회문)
회문(palindrome)은 앞 뒤 방향으로 볼 때 같은 순서의 문자로 구성된 문자열을 말한다. 

예를 들어 ‘abba’ ‘kayak’, ‘reviver’, ‘madam’은 모두 회문이다.

<br>

## 코드  

```java
int flag = 0;
for(int i =0;i<a.length()/2;i++) {
    if(arr[i] != arr[a.length()-i-1])
        flag = 1;
}
if(flag == 0)
    System.out.print("회문입니다.");
else
    System.out.print("회문이 아닙니다.");
    }
```


<br>

[출처]

- <https://javaprograming.tistory.com/51/>
