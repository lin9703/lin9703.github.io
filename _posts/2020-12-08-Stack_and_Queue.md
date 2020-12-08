---
layout: post
title: "스택(Stack)과 큐(Queue)"
author: "Lin"
tags: 자료구조
---
### CS Study Day 3 - Part1

<br>

Stack과 Queue는 선형 자료구조의 일종이다.

<br>

## Stack
- LIFO(Last In First Out) : 나중에 들어간 원소가 먼저 나온다.
- 안드로이드 액티비티를 관리할 때 스택 사용 
- 시간복잡도
    - 삽입 또는 삭제의 경우: O(1)
    - 검색: O(n)

<br>

## Queue
- FIFO(First In First Out) : 먼저 들어간 원소가 먼저 나온다.
- Java Collection에서 Queue는 인터페이스
- 활용 분야가 많으며 예시로 안드로이드에서 루퍼의 메시지 큐에 사용 
- 시간복잡도
    - 삽입 또는 삭제의 경우: O(1)
    - 검색: O(n)

<br>

### Stack 2개로 Queue 구현

{% highlight java %}
public class QueueUsingTwoStack {
    public static void main(String[] args) {
        QueueUsingStack queue = new QueueUsingStack();

        queue.push("A");
        queue.push("B");
        System.out.println(queue.pop());
        queue.push("C");
        System.out.println(queue.pop());
        System.out.println(queue.pop());
    }

    static class QueueUsingStack {
        static Stack inputStack;
        static Stack outputStack;

        QueueUsingStack() {
            inputStack = new Stack();
            outputStack = new Stack();
        }

        void push(Object s) {
            inputStack.push(s);
        }

        Object pop() {
            if (outputStack.isEmpty()) {
                while (!inputStack.isEmpty()) {
                    outputStack.push(
                            inputStack.pop()
                    );
                }
            }
            return outputStack.pop();
        }
    }
    
}
{% endhighlight %}




