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

