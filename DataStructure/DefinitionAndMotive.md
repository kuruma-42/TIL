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
