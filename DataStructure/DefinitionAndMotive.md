# Why I Start To Learn Data Structure 
- 더 나은 코드를 짜고 내가 하는 일에 자신감을 가지기 위해
- 어떤 코드가 좋은 코드인지 아닌지 알면서 일을 하기 위해 
- 프로그래밍을 하면서 느낌이나 감정으로 소통하지 않고 정확한 개념으로 소통하기 위해 
- Swift로 Data Structure 공부를 하려고 했는데 대부분 Java, C++, Python 자료다.
<br>
# What is Data Structure 
- 자료를 효율적으로 관리하는 기법

### Main Point 
- 리스트,트리 + 그래프 
<br>

### What is Data? 
- 컴퓨터에 저장할 수 있는 모든 값
- 컴퓨터에서 허용하는 형태의 값만 저장할 수 있음 -> 자료형
<br>

### What is Data Type?
- 컴퓨터에 저장할 수 있도록 프로그래밍 언어에서 미리 정의된 값들의 집합
- 시스템에서 제공하는 단위
- 사용자가 정의하는 단위
<br>

### 시스템에서 제공하는 자료형 (system-defined data type) 
#### 자료의 단위
- 비트 (Bit) : 0또는 1을 기록할 수 있는 최소 단위 
- 바이트 (Byte) -> 8bits : 1byte는 8bit로 구성
- 워드 (word) -> 4bytes or 8bytes : 컴퓨터의 내부에서 한번에 전송하거나 처리하는 단위 4byte(32bit) 또는 8bytes (64byte)가 많이 사용 

#### 자료의 구성
- 세상의 모든 자료는 문자와 숫자로 구성된다. 
- 문자 -> char, char *, String
- 숫자 -> 정수(int) or 실수(float) 

#### Char ( 문자 표현 )
ASCII code
- 8bit 영어, 숫자, 특수 문자를 표현하는 체계
- 7bits _ 1bit (parity 검사) 
- 표현할 수 있는 문자에 한게가 있다. 

Uni-code 
- 16bit로 세상의 모든 문자를 표현할 수 있는 체계

사용자가 정의하는 자료형 (user-defined data type)

하나의 자료는 다양한 자료형을 가진 요소들의 
집합으로 표현될 수 있다.

이러한 요소들의 집합으로 새로운 
자료형을 정의 (User or Student)

- struct (C언어)
- class (C++, Java, Python)


### What is Manipulation
- Insert
- Delete 
- Search
- Modify
- 추가 제거 검색 갱신등 많은 관리 작업이 가능 
- 가장 중요한 3연산: 추가, 제거, 검색
- 추가와 제거는 1번만 사용 가능
- 검색은 매우 빈번하게 사용 : 가장 중요한 작업은 검색이다. 

#### 검색의 3가지 종류 
- 주어지 집합에서 임의의 원소를 찾아라 (find arbitrary) 
- 주어진 집합에서 가장 먼저/늦게 온 원소를 찾아라 (Find Earliest / Last)
- 주어진 집합에서 top(최대/최소)인 원소를 찾아라(Find Top) 

### Technique
- 자료를 적절한 구조를 갖도록 조직하고 그에 따른 연산을 한다.

### Operation
- 자료를 관리하기 위한 작업 (추가, 제거, 검색, etc) 
- 구조는 달라도 연산은 동일함 -> 구조에 따른 연산의 구현 방법은 다름 

- 일차원 구조 -> List
- 계층 구조 -> Tree 

#### 구조 1: List 
- Ex) 자료 (명함들) 구조(리스트)

#### 구조 2: Sorted List 
- Ex) 자료 (명함들) 구조(정렬된 리스트) 
검색을 쉽게 하고 자료의 위치를 예측하기 위해 
정렬을 한다( 이름 순, 번호 순)

#### 구조 3: Queue
- Ex) 자료 (명항들 + 만난 순서) 구조 (큐)  



#### 구조 4:  Hierarchy
- Ex) 족보를 표현하는 방법 관계의 일관성을 표현할 수 있는 트리 구조가 필요하다 자료(족보) 구조(트리) 

#### 구조 5: Graph 
- 시각적 표현 (관계)


### Abstraction 
- 개별적인 사람이나 사물 상황의 성질부터 추출되어 가공된 일반적이고 공통적인 개념 


#### 자료구조에서의 추상화
- 매우 다양한 형태의 자료가 존재함
- 각 자료들의 개별적인 속성을 제거하고 공통된 속성을 추출하여 이를 이용하는 과정

Ex) 
다양한 자료 : 전화번호, 앱, 버스번호
공통된 속성 : 리스트로 관리
공통된 연산 : 추가, 제거, 검색, etc

#### 추상 자료형( abstract data type)
- 자료와 자료에 대한 연산들을 명기한 개념
- Class of objects whose logical behavior is defined by a set of values and set of operations
- Ex) class 안에 연산들을 묶었을 때 

#### 효율 (Efficiency)란 무엇인가?
- 어떤 성과(solution)을 얻기 위해서 얼마나 많은 자원 (resource)을 투입하였는지를 측정
- 성능(performance)라고도 함
- Efficiency or Performance = Solution / Resource

#### 효율(efficient)와 효과적(effective)
- 어떤 성과를 얻기 위해서 얼마나 많은 자원을 투입하였는지를 측정하는 점은 동일하다
- 효율적은 동일한 성과를 얻기 위해서 투입된 자원의 크기에 따라서 결정됨
- 효과적

#### 성능의 3가지 경우
- 최선의 경우 (Best case) => 최고기록 (기록중에 제일 좋은 기록만 기억) 
- 평균의 경우 (Average case) => 평점 (여러 과목의 점수들 중에서 평균점 산정)
- 최악의 경우 (Worst case) => 가장 긴 시간을 알려줌 
- “자료 구조에서의 성능은 최악의 경우에 대한 성능임” ( 최악의 경우에는 보장이라는 의미를 내포한다)

#### 컴퓨터의 자원 (resource)
- 시간 => CPU (이 프로그램은 10초 걸린다) 
- 공간 => Memory (이 프로그램은 100Mbyte의 메모리를 요구한다)
* CPU가 더 비싸고 발전이 느리기 때문에 시간에 대한 자원이 더 중요하다 

#### 자료 구조의 성능 
- 입력된 자료의 크기에 따라서 시간(공간)이 얼마나 필요할지 측정
- 입력된 자료의 크기가 증가할수록 요구되는 시간(공간)의 증가 속도를 표현

#### Summary 

자료를 효율적으로 관리하는 기법
일차원 구조 
리스트 
- Array
- Linked list
- Stack / Queue
* Sorting

계층 구조 
트리 
- Binary Search Tree 
- Priorty Queue
* Search

관계를 표현하고 정보를 추출하는 기법

그래프 
- Depth first traversal
- Breadth first traversal 





