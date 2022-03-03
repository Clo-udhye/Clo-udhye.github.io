---
layout: post
title: "연결 리스트(Linked List)"
tags: data-structure linked-list 
image: 
    path: /assets/img/datastructure/cover1.png
accent_color: '#F38181'
description: >
    자료구조: 연결리스트(Linked List)
categories:
    - study
    - data-structure
related_posts:    
    -    
---

# [DataStructure] 연결리스트(Linked List)
* 
{:toc}

## 개념
배열(Array)은 순차적으로 연결된 공간에 데이터를 나열하는 자료구조이고, 연결 리스트(Linked List)는 떨어진 곳에 존재하는 데이터를 화살표로 연결해서 관리하는 자료구조이다. 배열은 미리 특정한 연결된 공간을 확보하고 데이터를 쓰고 있는 자료구조이고, 연결 리스트는 필요할 때 마다 데이터를 추가할 수 있는 구조이다. 배열의 단점을 극복한 자료구조가 연결 리스트라고 볼 수 있다.

## 구조
연결리스트는 저장할 데이터와, 그 *다음에 나올 데이터가 저장되어있는 공간을 가리키는 주소값*(next)을 동시에 가지고 있다. 두 값은 하나의 데이터 단위인 노드(Node)에 저장해 관리된다.   
![노드](/assets/img/datastructure/node.png){: width="20%" height="20%"}   

Node는 Data와 주소값으로 구성이 되어 있고, 주소값은 각 node 안에서 다음에 연결된 node와의 연결 정보를 가지고 있는 공간이다. 연결 정보(next)는 다음 node의 데이터 주소를 말한다. 첫번째 데이터만 알고 있으면 주소값을 통해 그 다음으로 연결된 모든 데이터를 알 수 있다. 일반적으로 연결 리스트의 시작이 되는 node는 Head, 마지막 node는 Tail이라고 부른다.   
![리스트](/assets/img/datastructure/linkedlist1.png){: width="70%" height="70%"}   


## 연산
- `add(newNode)`  : 연결리스트에 새로운 노드 삽입
![add](/assets/img/datastructure/addnode.png){: width="70%" height="70%"} 
>- 새로 넣을 node의 앞쪽에 들어갈 node를 찾는다.   
>- 찾은 node의 next(node.next)에 저장되어있던 주소값을 newNode.next에 넣어 연결해준다.   
>- node.next에 newNode의 주소값을 넣어 연결한다.   

- `remove(node)`  : 연결리스트에 노드 삭제
![remove](/assets/img/datastructure/removenode.png){: width="70%" height="70%"} 
>- head 삭제 : head의 다음 node가 head로 변경 
>- tail 삭제 : tail 앞에 있는 node의 주소값을 null로 변경
>- 중간 node 삭제 : 삭제할 node를 찾는다. node의 주소값를 node.next에서 node.next.next로 바꾸어 연결해주고 node.next를 삭제

- `contain(data)` : 연결리스트안에 data를 가진 node가 있는지 찾는 연산 
>- 연결리스트의 head부터 시작해서 연결된 노드들을 조회하면서 원하는 data가 있는지 찾는다.
>- 연결리스트에 data가 있다면 `true`, 없다면 `false`를 리턴

## 구현
[소스코드](https://github.com/dev-dahye/dev-dahye.github.io)

## Java 클래스
java.util.LinkedList 
>extends AbstractSequentialList<E> 
 implements List<E>, Deque<E>, Cloneable, Serializable

### Method Summary 

|반환 타입|	Method |설명|
|---:|---|---|
|boolean |add(E e)       | 리스트의 끝에 해당 요소를 추가합니다|
|void    |add(int index, E element)|리스트의 지정된 위치에 해당 요소를 삽입합니다.|
|boolean |addAll(Collection<? extends E> c)| 지정된 컬렉션의 iterator가 반환한 순서대로 컬렉션의 모든 요소를 리스트의 끝에 추가합니다.|
|boolean |addAll(int index, Collection<? extends E> c)|지정된 위치에서 시작하여 지정된 컬렉션의 모든 요소를 ​​리스트에 삽입합니다.|
|void    |addFirst(E e)  |리스트의 시작 부분에 지정된 요소를 삽입합니다.|
|void    |addLast(E e)   |리스트의 끝 부분에 지정된 요소를 삽입합니다.|
|void    |clear()        |리스트의 모든 요소를 ​​제거합니다.|
|Object  |clone()        |리스트의 얕은 복사본(객체의 주소)을 반환합니다.|
|boolean |contains(Object o)|리스트에 지정된 요소가 포함되어 있으면 true를 반환합니다.|
|Iterator<E>|descendingIterator()|역방향 iterator를 반환합니다.|
|E       |element()      |리스트의 head(첫 번째 요소)를 검색하지만 제거하지는 않습니다.|
|E       |get(int index) | 리스트의 지정된 위치에 있는 요소를 반환합니다.|
|E       |getFirst()     |리스트의 첫 번째 요소를 반환합니다.|
|E       |getLast()      |리스트의 마지막 요소를 반환합니다.|
|int     |indexOf(Object o)|리스트에서 지정된 요소가 처음으로 나타나는 인덱스를 반환하거나 리스트에 요소가 없으면 -1을 반환합니다.|
|int     |lastIndexOf(Object o)|리스트에서 지정된 요소가 마지막으로 나타나는 인덱스를 반환하거나 리스트에 요소가 없으면 -1을 반환합니다.|
|ListIterator<E>|listIterator(int index)|리스트의 지정된 위치부터 list-Iterator를 반환합니다.|
|boolean |offer(E e)     |지정된 요소를 이 리스트의 tail(마지막 요소)로 추가합니다.|
|boolean |offerFirst(E e)|리스트의 맨 앞에 지정된 요소를 삽입합니다.|
|boolean |offerLast(E e) |리스트의 끝에 지정된 요소를 삽입합니다.|
|E       |peek()         |리스트의 head(첫 번째 요소)를 검색하지만 제거하지는 않습니다.|
|E       |peekFirst()    |리스트의 첫 번째 요소를 검색하지만 제거하지는 않습니다. 리스트가 비어 있으면 null을 반환합니다.|
|E       |peekLast()     |리스트의 마지막 요소를 검색하지만 제거하지는 않습니다. 리스트가 비어 있으면 null을 반환합니다.|
|E       |poll()         |리스트의 head(첫 번째 요소)를 검색하고 제거합니다.|
|E       |pollFirst()    |리스트의 첫 번째 요소를 검색하고 제거하거나 리스트가 비어 있으면 null을 반환합니다.|
|E       |pollLast()     |리스트의 마지막 요소를 검색하고 제거하거나 리스트가 비어 있으면 null을 반환합니다.|
|E       |pop()          |리스트가 나타내는 스택에서 요소를 팝합니다.|
|void    |push(E e)      |리스트가 나타내는 스택에 요소를 푸시합니다.|
|E       |remove()       |리스트의 head(첫 번째 요소)를 검색하고 제거합니다.|
|E       |remove(int index)|리스트의 지정된 위치에 있는 요소를 제거합니다.|
|boolean |remove(Object o)|지정된 Object가 존재하는 경우 리스트에서 지정된 요소의 첫 번째 발생을 제거합니다|
|E       |removeFirst()  |리스트에서 첫 번째 요소를 제거하고 반환합니다.|
|boolean |removeFirstOccurrence(Object o)|리스트에서 지정된 요소의 첫 번째 항목을 제거합니다(리스트를 처음부터 끝까지 순회할 때).|
|E       |removeLast()   |리스트에서 마지막 요소를 제거하고 반환합니다.|
|boolean |removeLastOccurrence(Object o)|리스트에서 지정된 요소의 마지막 항목을 제거합니다(리스트를 처음부터 끝까지 순회할 때).|
|E       |set(int index, E element)|리스트의 지정된 위치에 있는 요소를 지정된 요소로 바꿉니다.|
|int     |size()         |리스트의 요소 수를 반환합니다.|
|Object[]|toArray()      |리스트의 모든 요소를 ​​적절한 순서(첫 번째 요소에서 마지막 요소까지)로 포함하는 배열을 반환합니다.|
|<T>T[]  |toArray(T[] a) |리스트의 모든 요소를 ​​적절한 순서로 포함하는 배열을 반환합니다(첫 번째 요소에서 마지막 요소까지). 반환된 배열의 런타임 유형은 지정된 배열의 런타임 유형입니다.|
 




<br>
<br>

- - -

## Reference  
- <https://docs.oracle.com/javase/7/docs/api/> 
- <https://velog.io/@keemtj/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EB%A7%81%ED%81%AC%EB%93%9C-%EB%A6%AC%EC%8A%A4%ED%8A%B8Linked-List>
- <https://medium.com/@gwakhyoeun/til-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-linked-list-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-9b2fec70d272>