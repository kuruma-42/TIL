# Queue
- Queue 자료구조는 가장 먼저 들어온 값이 먼저 나가는 원칙 First-In First-Out 원칙에 따라
- 삽입(enqueue)과 삭제(dequeue) 연산이 이루어진다.
- 지원 연산은 enqueue, dequeue, isEmpty, front, len 이며 모두 O(1) 시간에 수행되어야 한다.
  - enqueue(val): 값 val을 오른쪽 끝 빈 칸에 삽입 (스택에서의 push와 완전 같은 연산이다)
  - dequeue(): 가장 왼쪽에 저장된(= 가장 오래된) 값을 삭제 후 리턴, 가장 오래된 값이 저장된 인덱스를 알고 있어야 한다. 이 인덱스를 front_index라고 하자
  - front(): 가장 왼쪽에 저장된(= 가장 오래된) 값을 (삭제하지 않고) 리턴


```python
class Queue:
    def __init__(self):
        self.items = []         # 데이터 저장을 위한 리스트 준비
        self.front_index = 0    # 다음 dequeue될 값의 인덱스 기억

    def __len__(self):
        return len(self.items)

    def enqueue(self, val):
        self.items.append(val)

    def dequeue(self):
        if self.front_index == len(self.items):     # 이 기준이 동작하는 이유
            print("Queue is empty")
            return None     # dequeue할 아이템이 없음을 의미

        else: # dequeue는 front_index를 조정해서 삭제 효과를 얻음
            x = self.items[self.front_index]
            self.front_index += 1 # 다음에 dequeue될 값의 인덱스 조정
            return x

    def front(self): # deqeue 코드와 동일하지만 front_index를 증가시키는 코드만 없다.
        if self.front_index == len(self.items):
            print("Queue is empty")
            return None

        else:
            x = self.items[self.front_index]
            return
```

- dequeue를 상수 시간에 하기 위해선, dequeue가 될 값의(index)를 저장하고 관리해야 한다.
- 상기의 코드에서 front_index 변수 -> dequeue가 되면 인덱스 값이 하나 증가하여 다음 dequeue될 예정인 값의 인덱스를 가리키도록 관리한다.
- self.front_index += 1 코드
- 주의 할 점은 실제로 삭제연산을 하면 알고리즘 문제를 풀 때 시간초과가 날 수 있다는 것이다.
