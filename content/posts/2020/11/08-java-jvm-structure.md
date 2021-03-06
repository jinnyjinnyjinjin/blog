---
title: "[Java] JVM 구조"
date: 2020-11-08T15:37:04+09:00
tags: [Java]
draft: true
---
프로그램이 실행되면 JVM은 시스템으로부터 프로그램을 수행하는데 필요한 메모리를 할당받고 JVM 은 이 메모리를 여러 영역으로 나누어 관리하는데, 그 중 3가지 주요 영역 (method area, call stack, heap) 을 살펴본다.

## 메서드 영역(method area)

프로그램 실행중에 어떤 클래스가 사용되면, JVM은 해당 클래스의 클래스파일(*.class)를 읽어서 분석하여 클래스에 대한 정보를 이곳에 저장한다. 이 때, 그 클래스의 클래스 변수(class variable)도 이 영역에 함께 생성된다.

## 힙(heap area)

인스턴스가 생성되는 공간. 인스턴스 변수들이 생성되는 공간이다.

## 호출스택(call stack 또는 execution stack)

메서드의 작업에 필요한 메모리 공간을 제공한다. 메서드가 실행되며 선언되는 지역변수들과 연산의 중간결과 등을 저하는데 사용되고 메서드가 작업을 마치면 메모리공간은 반환되어 비어진다.

- 메서드 호출 → 메모리를 스택에 할당 받음 → 수행 끝 → 메모리 반환 및 스택에서 제거
- 호출스택의 가장 상위에 있는 메서드가 현재 실행중인 메서드
- 가장 아래에 있는 메서드가 바로 위의 메서드를 호출한 메서드

## 기본형 매개변수와 참조형 매개변수

- **기본형 매개변수**: 변수의 값을 읽기만 할 수 있음
- **참조형 매개변수**: 변수의 값을 읽고 변경할 수 있음

**기본형 매개변수**
```java
public void method(int x) {
	//...
}
```
**참조형 매개변수**
```java
public void method(Car car) {
	//...
}
```

## 참조형 반환타입

- 반환타입이 참조형이라는 것은 메서드가 객체의 주소를 반환한다는 것을 의미

## 재귀호출

메서드의 내부에서 메서드 자신을 다시 호출하는 것을 재귀호출이라 하고, 재귀호출을 하는 메서드를 재귀 메서드라고 한다.

- 재귀 메서드의 경우 메소드가 호출 될때마다 메모리를 계속 할당 받아야 하기 때문에 반복문보다는 성능이 떨어질 수는 있지만 재귀호출이 주는 논리적 간결함이 장점이다.
- 반복문의 구조가 복잡해질 경우 재귀호출로 구현이 가능한지 고민이 필요하다.
- 성능보다 논리적 간결함이 주는 이득이 클 경우에만 사용한다.
- 무한호출을 방지하기 위해 확실한 조건을 주는 것과 매개변수의 유효성검사가 중요하다.

## 클래스 메서드(static 메서드)와 인스턴스 메서드

- **인스턴스 메서드** : 인스턴스를 반드시 생성 후에 호출이 가능한 메서드
- **클래스 메서드** : 인스턴스 생성 없이도 호출이 가능한 메서드

#### 메서드에 static 이 필요한 경우,

- 클래스의 멤버변수 중 모든 인스턴스에 공통된 값을 유지해야할 때.
- 인스턴스와 관계없을 경우. (인스턴스 변수나 인스턴스 메서드를 사용하지 않는)


> 출처: 자바의 정석
