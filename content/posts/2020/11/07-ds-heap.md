---
title: "[자료구조] Heap(힙)"
date: 2020-11-07T17:47:51+09:00
tags: [자료구조]
draft: false
---
### 이진 트리의 한 종류 (이진 힙 - binary heap)

1. 루트(root) 노드가 언제나 최댓값 또는 최솟값을 가짐
   - 최대 힙(max heap), 최소 힙(min heap)

2. 완전 이진 트리여야 함
   * 최대 힙(max) 힙
     * 부모 노드가 자식 노드보다 큰 값을 가지고 있음
     * 재귀적으로도 정의됨

### 이진 탐색트리와의 비교

1. 원소들은 완전히 크기 순으로 정렬되어 있는가?
   * 이진 탐색 트리에서는 그렇지만 최대 힙, 최소 힙에서는 그렇지 않고 느슨하게 정렬되어 있다.
2. 특정 키 값을 가지는 원소를 빠르게 검색할 수 있는가?
   * 이진 탐색 트리에서는 일반적으로 키 값으로 왼쪽 오른쪽을 찾아가기 때문에 빠르게 검색할 수 있지만 힙에서는 특정 키 값이 힙 안에 들어 있는가를 검색하는데에 좋은 방법이 없다.
3. 부가의 제약 조건은 어떤 것인가?
   * 힙은 이진 탐색 트리에서 완전 이진트리여야 한다는 부가적인 제약 조건을 가지고 있다.

### 최대 힙(Max Heap)의 추상적 자료구조

#### 연산의 정의

* `insert(item)` - 새로운 원소를 삽입
* `remove()` - 최대 원소(root node)를 반환함과 동시에 이 노드를 삭제

<p style="color: rgb(255, 51, 153);">순환이나 검색은 힙에서 얻을 수 있는 좋은 연산이 아님</p>

### 데이터 표현의 설계

#### 배열을 이용한 이진 트리의 표현
![max_heap](/images/2020/11/max_heap.jpeg)

#### 노드 번호 n을 기준으로
* 왼쪽 자식의 번호 = `2 * n`   
* 오른쪽 자식의 번호: `2 * n + 1`   
* 부모 노드의 번호: `n // 2`   

따라서 배열을 이용해 이진 트리를 구현할 수 있다.
![max_heap_array](/images/2020/11/max_heap_array.png)   

### 최대 힙에 원소 삽입

1. 트리의 마지막 자리에 새로운 원소를 임시로 저장
   * 완전 이진 트리의 성질을 만족
2. 부모 노드와 키 값을 비교하여 위로, 위로, 이동

#### 복잡도

##### 원소의 개수가 n인 최대 힙에 새로운 원소 삽입
➡️ 부모 노드와의 대소 비교 최대 회수 최악 복잡도:   
![complexity](/images/2020/11/complexity.jpeg)

### 최대 힙에서 원소의 삭제

1. 루트 노드의 제거 - 이것이 원소들 중 최댓값
2. (루트 노드를 제거 했을 때에도 완전 이진 트리를 만족하기 위해서) 트리 마지막 자리 노드를 임시로 루트 노드의 자리에 배치
3. (아직 최대값이 아닐 수도 있기 때문에) 자식 노드들과의 값 비교 후 아래로, 아래로 이동
   * 자식은 둘 있을 수도 있는데, 어느 쪽으로 이동?
    ➡️ 둘 중에 더 큰 값을 기준으로 임시로 배치된 노드가 아래로 이동하게 된다.

#### 복잡도

##### 원소의 개수가 n인 최대 힙에서 원소 삭제
➡️ 자식 노드들과의 대소 비교 최대 회수 최악 복잡도:   
![complexity](/images/2020/11/complexity.jpeg)

### 최대/최소 힙의 응용

#### 우선 순위 큐 (priority queue)   
➡️ Enqueue 할 때, `느슨한 정렬` 을 이루고 있도록 함: **O(logN)**   
➡️ Dequeue 할 때, 최댓값을 순서대로 추출: **O(logN)**   

#### 힙 정렬(heap sort)   
➡️ 정렬되지 않은 원소들을 아무 순서로나 최대 힙에 삽입: **O(logN)**   
➡️ 삽입이 끝나면, 힙이 비게 될 때까지 하나씩 삭제: **O(logN)**   
➡️ 원소들이 삭제된 순서가 원소들의 정렬 순서   
➡️ 정렬 알고리즘의 복잡도: **O(NlogN)**   

<br>
<br>

>참조: [어서와! 자료구조와 알고리즘은 처음이지?](https://programmers.co.kr/learn/courses/57)