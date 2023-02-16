# Process Synchronization 1

- 다중 프로그래밍 시스템
    - 여러 개의 프로세스들이 존재
    - 프로세스들은 서로 독립적으로 동작
    - 공유 자우너 또는 데이터가 있을 때, 문제 발생 가능
- 동기화 
    - 프로세스 들이 서로 동작을 맞추는 것 
    - 프로세스 들이 서로 정보를 공유하는 것
    - ‘ 대화하는 행위라고 생각하면 된다 ‘ 


Asynchronous and Concurrent P’s
- 비동기적(Asynchronous)
    - 프로세스들이 서로에 대해 모름
- 병행적(Concurrent)
    - 여러 개의 프로세스들이 동시에 시스템에 존재
- 병행 수행중인 비동기적 프로세스들이 공유 자원에  동시에 접근 할 때 문제가 발생할 수 있음 (동시에 작업을 하고있는데 서로 모르는 상황이기 때문이다) 

Terminologies
- Shared data(공유 데이터) Or Critical data
    - 여러 프로세스들이 공유하는 데이터
- Critical section(임계영역)
    - 공유 데이터를 접근하는 코드 영역(code segment)
- Mutual exclousion(상호배제)
    - 둘 이상의 프로세스가 동시에 critical section에 집입하는 것을 막는 것 

Note
기계어 명령 (machine instruction)의 특성
- Atomicity(원자성), indivisible (분리 불가능)
- 한 기계어 명령의 실행 도중에 인터럽트 받지 않음 

Mutual Exclusion (상호배제) 
- 어떤 프로세스가 임계 영역(Critical Section)에 진입해 있다면 다른 프로세스의 접근을 허용하면 안 된다. 

Mutual Exclusion Methods 
- Mutual Exclusion Primitives
    - enterCS() primitive
        - Critical section 진입 전 검사
        - 다른 프로세스가 critical section 안에 있는지 검사 
        - Ex) 화장실 안에 누가 있는지 노크하는 개념 
    - exitCS() primitive 
        - Critical section을 벗어날 때의 후처리 과정
        - Critical section을 벗어남을 시스템이 알림 
        - Ex) 화장실 다 쓰고 나간다고 알려주는 개념 

** Primitive란? 
- 가장 기본이 되는 연산이라는 뜻으로 해석
- 어떤 모듈을 만들 때 기본이 되는 연산 
- ‘기본 연산’ 이라고 생각하면 편할 것이다. 


Requirements for ME primitives 
- Mutual exclusion (상호배제) 
    - Critical section (CS) 에 프로세스가 있으면, 다른 프ㅜ로세스의 진입을 금지 
- Progress (진행)
    - CS 안에 있는 프로세스 외에는, 다른 프로세스가 CS에 진입하는 것을 방해 하면 안 됨 
- Bounded waiting (한정대기)
    - 프로세스의 CS 진입은 유한시간 내에 허용되어야 함 
