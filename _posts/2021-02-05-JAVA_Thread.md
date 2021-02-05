---
layout: post
title: "Java에서 Thread"
author: "Lin"
tags: JAVA
---
### CS Study Day 14 - Part5

<br>

요즘 OS는 모두 멀티태스킹을 지원한다.
```
멀티 태스킹이란?
두 가지 이상의 작업을 동시에 하는 것
예를 들어, 컴퓨터로 음악을 들으면서 웹서핑도 하는 것
```

- 동시에 처리될 수 있는 프로세스의 개수는 CPU 코어의 개수와 동일한데, 많은 개수의 프로세스가 존재하기 때문에 모두 동시에 처리할 수 없다. <br>
-> 각 코어들은 아주 짧은 시간동안 여러 프로세스를 번갈아가며 처리하여 동시 동작하는 것처럼 보이게 한다.
- 이와 마찬가지로, 멀티스레딩이란 `하나의 프로세스 안에 여러 개의 스레드가 동시에 작업을 수행`하는 것을 말한다. <br>
-> 스레드는 `하나의 작업단위`이다.

<br>

## Java에서 Thread 구현 방법 
자바에서 스레드 구현 방법은 2가지가 있다.
1. Runnable 인터페이스 구현
2. Thread 클래스 상속

둘 다 run() 메소드를 Overriding 한다.

<br>

### Thread 생성
위의 두 가지는 인스턴스 생성 방식에 차이가 있다.

#### [Runnable 인터페이스 구현]

```java
public class MyThread implements Runnable {
  @Override
  public void run(){
    // 수행 코드.
  }
}
```
```java
public static void main(String[] args) {
    Runnable r = new MyThread();
    Thread t = new Thread(r, "mythread");
}
```
- MyThread에서 run() 메소드를 Override
- start() 메소드가 없기 때문에 MyThread를 인스턴스화해서 Thread 생성자에 argument로 넘겨줘야 한다.
- 다른 클래스 상속 가능 

<br>
#### [Thread 클래스 상속]

```java
public class MyThread extends Thread {
  public void run(){
    // 수행 코드.
  }
}
```
- run() 메소드 직접 구현 
- 상속받은 클래스 자체를 스레드로 사용 
- 다른 클래스 상속 불가능 (다중 상속 불가능)

<br>
> Thread 클래스를 상속받으면 스레드 클래스의 메소드(ex: getName())를 바로 사용할 수 있지만, 
> Runnable 인터페이스 구현의 경우에는 Thread 클래스의 static 메소드인 currentThread()를 호출해
> 현재 스레드에 대한 참조를 얻어야만 호출이 가능 

<br>

### Thread 실행
`스레드의 실행은 run() 호출이 아닌 start() 호출로 해야 한다.`

**왜?** <br>
run() 메소드로 작업을 지시해도 똑같이 작업을 한다. <br>
**그러나, run() 메소드로 실행한다면, 스레드를 사용하는 것이 아니다.**

Java에는 콜 스택(call stack)이 있다. 
> 콜 스택: 실질적인 명령어를 담고 있는 메모리로, 하나씩 꺼내서 실행시키는 역할 

만약 동시에 두 가지 작업을 한다면, 두 개 이상의 콜 스택이 필요하게 된다. <br>
`스레드를 이용한다는 건, JVM이 다수의 콜 스택을 번갈아가며 일처리`하고 사용자에게 동시에 작업하는 것처럼 보여주는 일이다.

즉, run() 메소드를 이용하는 것은 main()의 콜 스택 하나만 이용하는 것으로 스레드 활용이 아니다. <br>
(그냥 스레드 객체의 run이라는 메소드를 호출하게 되는 것)

start() 메소드를 호출하면, JVM은 스레드를 위한 콜 스택을 새로 만들어주고 context switching을 통해 스레드답게 동작하게 해준다. <br>

-> 결론: `start()는 스레드가 작업을 실행하는데 필요한 콜 스택을 생성한 다음 run()을 호출해서 그 스택 안에 run()을 저장할 수 있도록 해준다.`

<br>

### Thread 실행제어
> 스레드의 상태는 5가지가 있다.
- NEW: 스레드가 생성되고 아직 start()가 호출되지 않은 상태
- RUNNABLE: 실행 중 또는 실행 가능 상태
- BLOCKED: 동기화 블럭에 의해 일시정지된 상태(Lock이 풀릴 때까지 기다림)
- WAITING, TIME_WAITING : 실행 가능하지 않은 일시정지 상태
- TERMINATED : 스레드 작업이 종료된 상태

스레드는 이와 같이 다양한 상태를 가지고 있으며, 이를 잘 사용하기 위해 `동기화`와 `스케줄링`이 필요하다.
- 스케줄링과 관련된 메소드 : sleep(), join(), yield(), interrupt()
- start() 이후에 join()을 해주면 main 스레드가 모두 종료될 때까지 기다려주는 일도 해준다.

<br>

## 동기화(Synchronized)
`여러 스레드가 같은 프로세스 내의 자원을 공유하면서 작업할 때 서로의 작업이 다른 작업에 영향을 주기` 때문에 멀티스레딩 환경에서 동기화는 필수적이다.

<br>
#### 스레드 동기화 방법
- 임계 영역(critical section): 공유 자원에 단 하나의 스레드만 접근하게 함 (하나의 프로세스에 속한 스레드만 가능)
- 뮤텍스(mutex): 공유 자원에 단 하나의 스레드만 접근하게 함 (서로 다른 프로세스에 속한 스레드도 가능)
- 이벤트(event) : 특정한 사건 발생을 다른 스레드에게 알림
- 세마포어(semaphore) : 한정된 개수의 자원을 여러 스레드가 사용하려고 할 때 접근 제한
- 대기 가능 타이머(waitable timer) : 특정 시간이 되면 대기 중이던 스레드 깨움

<br>

### synchronized 활용
> synchronized를 활용해 임게영역 설정 가능 

필드에 Collection이 불가피하게 필요할 때 
Java에서는 `synchronized` 키워드를 사용하여 스레드 간의 race condition을 통제한다. <br>
-> 이 키워드로 구현된 Collection들도 많이 존재한다. (List 대신 Vector, Map 대신 HashTable) <br>
-> 그러나 이 Collection들은 제공하는 API가 적고 성능도 좋지 않다.

기본적으로는 `Collections`라는 util 클래스에서 제공하는 static 메소드를 통해 해결 가능
- `Collections.synchroziedList()`, `Collections.synchroziedSet()`, `Collections.synchroziedMap()` 등이 존재
- JDK 1.7 부터는 `concurrent package`를 통해 `ConcurrentHashMap`이라는 구현체 제공
    - Collections util을 사용하는 것보다 synchronized 키워드가 적용된 범위가 좁아서 보다 좋은 성능
    
<br>

### ThreadLocal
- 스레드 사이에 간섭이 없어야 하는 데이터에 사용 
- 스레드 내부의 싱글톤을 사용하기 위해 사용 <br>
(멀티스레드 환경에서 클래스의 필드에 멤버를 추가할 수 없고 매개변수로 넘겨받아야 하기 때문에)
- 주로 사용자 인증, 세션 정보, 트랜잭션 컨텍스트에 사용 

#### 사용 방법
1. ThreadLocal 객체를 생성한다.
2. ThreadLocal.set() 메서드를 이용해서 현재 스레드의 로컬 변수에 값을 저장한다.
3. ThreadLocal.get() 메서드를 이용해서 현재 스레드의 로컬 변수 값을 읽어온다.
4. ThreadLocal.remove() 메서드를 이용해서 현재 스레드의 로컬 변수 값을 삭제한다.

