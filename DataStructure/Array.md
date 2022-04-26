# Array

### 리스트는?
- 가장 기초적이고 오랫동안 사용된 자료구조
- 원소를 한 줄로 나열한 구조 (특별한 순서를 따름)
- 目録라고도 함
- 유한한 원소들의 나열 (a finite sequence of elements)
- Ex) A = (2, 3, 4, 5, 7, 13, 17, 19)
- 각 원소들은 인덱스에 대응됨(index -> element) * 리스트의 가장 중요한 성질
- n개의 원소가 있다면 인덱스는 n-1까지 사용됨
- (인덱스, 원소)의 쌍으로 저장함

### 리스트의 구현 방법 
#### 배열 (Array): 인덱스에 기반한 구현 
- 연속된 기억 공간에 원소를 저장
- 인접한 원소는 인접한 주소에 저장
- 메모리에 배열의 크기보다 더 큰 연속된 공간이 허용될 때 사용

#### 연결 리스트(Linked list)
- 메모리의 배열의 크기보다 더 큰 연속된 공간이 없을 때 사용
- 한 원소는 다음 원소를 가리키는 링크를 가지고 있음

### 2가지 리스트

#### 정렬된 리스트 
- Ex) A = A = (2, 3, 4, 5, 7, 13, 17, 19)
- 원소의 위치를 예측할 수 있음
- 검색에 유리하다
- 추가에 불리하다
- 제거에 불리하다
#### 정렬되지 않은 리스트 
- Ex) A = A = (11, 19, 5, 2, 7, 13, 17, 3)
- 원소의 위치를 예츨할 수 없음
- 검색에 불리하다
- 추가에 유리하다
- 제거에 유리하다 

#### 이렇게 보면 정렬된 리스트가 더 안 좋은 것 같지만
#### 추가와 제거는 한 번 일어나지만 검색은 매우 빈번하게 일어나기 때문에 정렬된 리스트가 더욱 좋다 라고 말 할 수 있다.

### 리스트의 종류
- 원소를 저장하는 리스트 : 배열 / 연결 리스트
- 원소와 순서를 저장하는 리스트: 스택 / 큐 

### 배열(Array)
- 리스트를 index를 이용해서 구현한 구조
- 연속적으로 할당된 기억 공간 
- 모든 프로그래밍 언어에서 기본적으로 제공
- 배열의 모든 원소들은 index에 대응됨 
- n개의 자료를 하나의 주소로 접근할 수 있음

### 메모리에서 배열의 구현
- Int mylist[5]; [0] ~ [4]
- mylist의 주소가 23040이라면 
- 23040의 주소에 1,2,3,4를 더하면 mylist의 주소 (23040)로 5개의 원소에 접근할 수 있다.
- *n 개의 자료를 하나의 주소로 접근할 수 있다는 말이다.

### 배열과 친구들 (구현 팁)
- 배열과 함께 벼읠의 크기 및 현재 저장된 원소의 개수를 함께 생각할 것 
- arr: 배열
- size: 배열의 크기 ( 할당 받은 메모리의 크기)
- count: 현재 배열의 저장된 원소의 수
- count <= size
- 반드시 0으로 초기화해서 사용할 것 

### 정적 배열(static array) 
- 컴파일 될 때 할 때 기억 공간을 할당 받는 배열
```Swift 
#define Size 100
{
    int count = 0;
    Int arr[Size];
}
```

### 동적 배열(dynamic array)
- 실행될 때 기억 공간을 할당 받는 배열
```Swift 
#define Size 100
{
    int count = 0;
    Int *arr - calloc ( Size, sizeof(int) );
}
```

#### 기본 연산 (프로그래밍 언어에서 제공)
- 생성 (create) : n개의 원소를 저장할 수 있는 배열 공간을 할당
- 인출 (retrieve) : 배열의 i번째 원소를 읽어옴
- * 인출은 검색과 비슷한 일을 기능을 하는 것 같으나 검색은 원소를 주고 원소의 index를 알기 위한 것이고, 인출은 index를 주고 원소 값을 아는 것을 말한다. 
- 저장 (store) : 원소를 x 배열의 I 번째 위치에 저장
- * 저장은 추가 연산과 같은 것 같으나 추가 연산은 원소가 제거되지 않는다. 그렇지만 저장은 기존의 원소가 사라진다.

#### 추가 연산들 
- 검색 (search)
- 추가 (insert)
- 제거 (delete)
- 크기(size)
- 풀 (isFull)
- 엠티 (isEmpty)


### 검색 (Search)의 정의

성공한 검색 
- Key Element가 배열에 있는 경우
실패한 검색
- Key Element가 배열에 없는 경우

선형 검색 (linear search)
- 완전 검색 (exhaustive search) 또는 순차 검색 (sequential search)
- 배열의 첫 번째 원소부터 차례로 방문하면서 key element와 동일한 원소가 있는지 확인 
- 정렬되지 않은 배열에서도 적용할 수 있다. 

i번째 원소와 key element의 비교 -> 같으면 i를 리턴 
모든 원소 (0 ~ n - 1 번째)에 대해서 비교 
끝까지 같은 원소를 찾지 못했으면 -> -1을 리턴 (실패) 

```swift
index linear_search( Array arr, elt x )
for( int i = 0; i < n; i++) {
    if (arr[i] == x)
    return i;
}

return -1; // Null
```

선형 탐색의 시간 복잡도(time complexity)는?
- 최악의 경우 : O(n)
- 평균의 경우 : O(n/2) -> O(n)
- 최선의 경우 : O(1)

이진 검색 (binary search) 
- 분할 정복 (divide & conquer) 알고리즘
- 배열의 중간 원소 (mid element)와 key element를 비교하여 배열을 분할함으로써 검색을 수행
- 정렬된 배열에서만 적용할 수 있음 



### Definition
- 데이터가 많아지면 그룹 관리의 필요성이 생긴다. 
- 여러 데이터를 하나의 이름으로 그룹핑해서 관리하기 위한 데이터 스트럭쳐이다.

```swift
iosDeveloper[0] = "kuruma42"
iosDeveloper[1] = "dusy93"
```
- 상기의 코드에서 0,1에 해당하는 고유의 번호는 우리는 index라고 한다. 
- 한 반의 학생들에게 각각 번호를 부여하는 것과 같은 행위이다. 
- index를 통해서 데이터를 저장하고 데이터를 가져올 수 있는 것이 배열의 가장 중요한 특징이다.
- 상기의 코드에서 "kuruma42", "dusy93"은 value라 하고 
- index와 value가 결합 되어있는 것을 element라 한다. 

### Advantage
- 데이터를 그룹으로 관리하기 좋다. 
- 그룹에 속해있는 element들만 처리하기 좋은데 그 때 사용하는 기법이 반복문이다. 
- 배열에 저장되어 있는 값들을 하나하나 꺼내서 각각의 값에 대해서 처리 할 수 있는 것이 배열과 반복을 같이 써서 만들어 낼 수 있는 중요한 기능, 효과라고 할 수 있다. 

### Study Way 
- 대부분의 Data Structure 강의나 자료들은 대부분 Java, C++, Python등의 언어로 되어있다.
- 나는 이러한 강의들에서 가르쳐 주는 것 들을 Swift로 컨버팅 할 생각이다. 
- Apple 공식 문서를 참고하여 학습을 진행하겠다. 
- [Array : Apple Docs](https://developer.apple.com/documentation/swift/array)
- 

### Definition in Swift
- An ordered, random-access collection.
- 정렬된 랜덤액세스 콜렉션이다. 

### Declaration
```swift
@frozen struct Array<Element>
```
- swift의 모든 데이터 타입은 구조체로 되어있다고 배웠는데 이 곳에서도 확인할 수 있다.
- 개발을 하다보면 swift는 정말 많은 형태로 배열을 선언할 수 있다. 예시는 잠시 후 살펴보겠다.

### OverView 
- 배열은 우리가 앱 개발을 하면서 가장 일반적으로 쓰는 데이터 타입이다. 우리는 배열을 우리의 앱의 데이터를 조직화하기 위해서 사용한다. 구체적으로, 우리는 배열 타입을 element들의 타입을 하나의 타입으로 고정하기 위해 사용한다. 배열은 모든 종류의 elements를 저장할 수 있다. - integers 부터 string 그리고 class 까지도 저장할 수 있다. 
- Swift는 문법적으로 배열을 쉽게 만둘 수 있다. 간단하게 쉼표로 구분된 값 목록을 대괄호로 묶기만 하면 된다. 다른 어떤 정보 없이도, Swift는 자동적으로 배열의 element 타입을 추론해 구체화된 값이 포함된 배열을 만들어준다. 

### Example 
```swift
// An array of 'Int' elements
let oddNumbers = [1, 3, 5, 7, 9, 11, 13, 15]

// An array of 'String' elements
let streets = ["Albemarle", "Brandywine", "Chesapeake"]

// Shortened forms are preferred
var emptyDoubles: [Double] = []

// The full type name is also allowed
var emptyFloats: Array<Float> = Array()

var digitCounts = Array(repeating: 0, count: 10)
print(digitCounts)
// Prints "[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]"
```

### Accessing Array Values 
- 전 배열에 걸쳐서 어떤 기능을 수행할 필요가 있다면, 반복을 위해 for-in loop를 사용해라 

```swift
for street in streets {
 print("I don't live on \(street).")
}
// Prints "I don't live on Albemarle."
// Prints "I don't live on Brandywine."
// Prints "I don't live on Chesapeake."
```
- isEmpty를 사용하여 배열에 element가 있는지 확인하고 count 프로퍼티를 사용하여 몇 개의 element가 있는지 빠르게 확인하라 

```swift
if oddNumbers.isEmpty {
    print("I don't know any odd numbers.")
} else {
    print("I know \(oddNumbers.count) odd numbers.")
}
// Prints "I know 8 odd numbers."
```

- 각각의 배열의 elements에 subscript를 통해 접근할 수 있다. 비어있지 않은 배열의 첫 번째 element의 인덱스는 항상 0이다. 우리는 0부터 배열의 element의 수까지 포함해 subscript로 만들 수 있다. 음수를 쓰거나 배열의 수 보다 같거나 큰 인덱스는 런타임 에러를 발생시킨다. 

```swift
print(oddNumbers[0], oddNumbers[3], separator: ", ")
// Prints "1, 7"

print(emptyDoubles[0])
// Triggers runtime error: Index out of range
```


