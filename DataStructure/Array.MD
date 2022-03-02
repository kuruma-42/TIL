# Array
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


