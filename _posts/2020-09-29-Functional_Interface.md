---
layout: post
title: "함수형 인터페이스 (Functional Interface)"
author: "Lin"
tags: JAVA
---


## 함수형 인터페이스 (Functional Interface)
1개의 추상 메소드를 갖고 있는 인터페이스<br/>
아래와 같은 인터페이스를 함수형 인터페이스라고 한다.

    public interface FunctionalInterface {
        public abstract void doSomething(String text);
    }
  
사용 이유: 자바의 람다식은 함수형 인터페이스로만 접근 가능<br/>
다음과 같은 방식으로 사용 가능하다.

    public interface FunctionalInterface {
         public abstract void doSomething(String text);
    }
    
    FunctionalInterface func = text -> System.out.println(text);
    func.doSomething("do something");

<br>

### 기본 함수형 인터페이스
자바에서 기본적으로 제공하는 함수형 인터페이스는 다음과 같다.
- Runnable
- Supplier
- Consumer
- Function<T, R>
- Predicate

#### Runnable
인자를 받지 않고 리턴값도 없는 인터페이스

    public interface Runnable {
      public abstract void run();
    }
    
    /* 사용 에시 */
    Runnable runnable = () -> System.out.println("run anything!");
    runnable.run();
    // 결과
    // run anything!
    
#### Supplier<T>
인자를 받지 않고 T 타입의 객체를 리턴

    public interface Supplier<T> {
        T get();
    }
    
    /* 사용 예시 */
    Supplier<String> getString = () -> "Happy new year!";
    String str = getString.get();
    System.out.println(str);
    // 결과
    // Happy new year!
    
#### Consumer<T>
T 타입의 객체를 인자로 받고 리턴 값은 없다.

    public interface Consumer<T> {
        void accept(T t);
    
        default Consumer<T> andThen(Consumer<? super T> after) {
            Objects.requireNonNull(after);
            return (T t) -> { accept(t); after.accept(t); };
        }
    }
    
    /* 사용 예시 */
    Consumer<String> printString = text -> System.out.println("Miss " + text + "?");
    printString.accept("me");
    // 결과
    // Miss me?
    
#### Function<T, R>
T 타입의 인자를 받고, R 타입의 객체를 리턴

    public interface Function<T, R> {
        R apply(T t);
    
        default <V> Function<V, R> compose(Function<? super V, ? extends T> before) {
            Objects.requireNonNull(before);
            return (V v) -> apply(before.apply(v));
        }
    
        default <V> Function<T, V> andThen(Function<? super R, ? extends V> after) {
            Objects.requireNonNull(after);
            return (T t) -> after.apply(apply(t));
        }
    
        static <T> Function<T, T> identity() {
            return t -> t;
        }
    }
    
    /* 사용 예시 */
    Function<Integer, Integer> multiply = (value) -> value * 2;
    Integer result = multiply.apply(3);
    System.out.println(result);
    // 결과
    // 6
    
#### Predicate<T>
T 타입 인자를 받고 결과로 boolean을 리턴

    public interface Predicate<T> {
        boolean test(T t);
    
        default Predicate<T> and(Predicate<? super T> other) {
            Objects.requireNonNull(other);
            return (t) -> test(t) && other.test(t);
        }
    
        default Predicate<T> negate() {
            return (t) -> !test(t);
        }
    
        default Predicate<T> or(Predicate<? super T> other) {
            Objects.requireNonNull(other);
            return (t) -> test(t) || other.test(t);
        }
    
        static <T> Predicate<T> isEqual(Object targetRef) {
            return (null == targetRef)
                    ? Objects::isNull
                    : object -> targetRef.equals(object);
        }
    }
    
    /* 사용 예시 */
    Predicate<Integer> isBiggerThanFive = num -> num > 5;
    System.out.println("10 is bigger than 5? -> " + isBiggerThanFive.test(10));
    // 결과
    // 10 is bigger than 5? -> true

<br>
<br>
[참고 블로그](https://codechacha.com/ko/java8-functional-interface/)


