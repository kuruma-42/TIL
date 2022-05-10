# 연결리스트 (Linked List)

리스트의 정의 (복습)
- 유한한 원소들의 나열 (a finite sequence of elements)
- 각 원소들읜 인덱스에 대응됨 (index -> element)
- 2가지 형태의 구현
- * 인덱스 기반 구현 -> 배열
- * 포인터 기반 구현 -> 연결 리스트 

배열 (복습) 
- 원소들이 메모리에서 일정한 (a fixed distance)으로 나열되어있다.

연결 리스트 
- 원소들이 메모리에서 임의의 위치(at arbitrary position)에 배치되어 있음
- 한 원소는 다음 원소를 기리키는 link를 가지고 있음
- “data + link -> node” 

||배열|연결 리스트|
|:---|:---|:---|
|메모리 공간|연속된 메모리 주소|이산된 메모리 주소|
|공간할당|정적 할당/ 동적 할당|동적 할당 
|접근 경로|첫 번째 원소의 주소|첫 번째 원소의 주소|
|접근 방법|인덱스|포인터| 
|접근 방식|Random access|Sequential access|

* Random access의 의미 : 원소의 위치와 접근 시간의 연관성이 없다
* a[0] = a(n)

* Sequential access의 의미 : 접근 시간이 원소의 위치에 의해서 결정됨. 
* 첫 번째 원소는 바로 접근이 가능하지만 n번째 원소는 link를 따라서 가야지만 알 수 있다.

연결 리스트의 장점 
- 연속된 메모리를 가지지 않아도 사용가능

배열의 장점 
- Random access가 가능해서 빠르다. 


연결 리스트 정의
- node = data + link
- node는 메모리의 임의의 위치에 배치됨
- 각 node는 다음 node를 가리키는 link를 포함하고 있음
- 연결리스트는 실제로 정의를 할 때 실제로 정의 하는 게 아니라 node만 구현하면 된다.

구조체와 클래스를 이용한 정의 
```c
typedef struct _node node;
struct _node {
    char ats[3]; 
    node *link; 
}; 
```

```c
class node {
    char ats[3];
    node *link; 
}; 
```

단일 연결 리스트(singly linked list)
- 각 node는 하나의 link를 가짐(next 또는 rlink)
- chain

이중 연결 리스트(doubly linked list)
- 각 node는 두 개의 link를 가짐 (nextlink, rlink, prev 또는 link)
