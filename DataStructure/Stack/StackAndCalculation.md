# Stack 1 
스택 (stack)의 개념
* 원소를 그 도착한 시간의 반대 순서를 저장한 리스트 
* 원소의 추가와 제거가 탑 (top)이라고 불리우는 한 끝에서만 일어나는 리스트
* (A list in which insertions and deletions are made at one end called the top)
    * 가장 마지막에 들오어면 가장 먼저 제거됨
    * 가장 먼저 들어오면 가장 마지막에 제거됨
    * Last-in First-out ( LIFO 또는 FILO )
* 원소를 추가하는 연산: Push
* 원소를 제거하는 연산: Pop

스택의 자료구조 
* Size(스택에 저장할 수 있는 원소의 수)
* List of elements (원소를 저장하는 리스트)
* Top (top의 위치를 나타내는 값) 

```c
class Stack {
	int Size;
	DataType *Items;
	int TOP;
};
```
스택의 연산
* 생성 (createStack)
    * 지정된 크기의 원소를 저장하는 스택을 할당
* 엠티 (IsEmpty)
    * 스택에 원소가 없으면 True를 리턴
* 풀 (IsFull)
    * 스택에 더 원소를 넣을 수 없으면 True를 리턴
* 추가 (Push)
    * 스택에 새로운 원소를 삽입
* 제거 (Pop)
    * 스택에서 원소를 삭제 
* *스택에서는 검색 연산 X 탑에 있는 것만 볼 수 있다.
