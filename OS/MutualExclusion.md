# MutualExclusion 
### Spin Lock 
- 정수 변수
- 초기화, P(), V() 연산으로만 접근 가능
    - 위 연산들은 indivisible( or atomic) 연산
        - OS support: P나 V연산을 할 때는 Preemption시키지 안흔다는 보장을 해줌
        - 전체가 한 instruction cycle에 수행 됨 
- 멀티 프로세서 시스템에서만 사용가능 ( CPU가 n개 있어야지 bounded wating 조건을 침해하지 않음)
- Busy Waiting ( 기다릴 때도 계속 돌아서 자원 낭비 )

### Semaphore 
- 1965 Dijkstra가 제안 
- Busy Waiting 문제 해결 
- 음이 아닌 정수형 변수(S)
    - 초기화 연산, P(), V() 로만 접근 가능
        - P: Probern(검사)
        - V: Verhogen (증가) 
    - 임의의 s 변수 하나에 ready queue 하나가 할당 됨 

Binary semaphore
- S가 0과 1 두 종류의 값만 갖는 경우
- 상호배제나 프로세스 동기화의 목적으로 사용

Counting semaphore
- S가 0이상의 정수값을 가질 수 있는 경우
- Producer-Consumer 문제 등을 해결하기 위해 사용
    - 생산자 소비자 문제 

Description 
- 초기화 연산
    - S 변수에 초기값을 부여하는 연산
- P() 연산, V() 연산
    - SpinLock 같은 경우는 Busy Waiting이 발생하지만
    - Semaphore의 경우는 Queue 대기에 기다리게 된다. 
    - 작업이 끝나면 대기실 Queue에 기다리던 Process를 WakeUp 시킨다. 
- 모두 indivisible 연산 
    - OS support ( 나눌 수 없는 연산이고 OS 가 이를 지원한다 ) 
    - 전체가 한 instruction cycle에 수행 됨

Semaphore로 해결 가능한 동기화 문제들 
- 상호배제 문제
    - Mutual exclusion 
- 프로세스 동기화 문제
    - Process synchronization problem
        - Process들의 실행 순서 맞추기
            - 프로세스들은 병행적이며, 비 동기적으로 수행
        - Sync라는 변수를 주고 0으로 Setup 
        - 이미 CS를 사용중인 프로세스에서 Sync변수에 1을 반남하는 V(sync)를 수행
        - 반납되면 기다리던 Process가 실행된다. 
- 생산자 소비자 문제
    - Producer consumer problem
    - 생산자(Producer) 프로세스
        - 메세지를 생성하는 프로세스 그룹
    - 소비자 프로세스
        - 메세지를 전달받는 프로세스 그룹 
    - 생산자가 생산을 하고 놓으려고 할 때 누군가 생산된 것을 가져가면 안 되고 
    - 생산자가 생산을 하고 놓으려고 할 때 다른 생산자가 같은 곳에 놓으려고 하면 안 되고 
- Reader-writer 
    - Reader
        - 데이터에 대해 읽기 연산만 수행
    - Writer 
        - 데이터에 대해 갱신 연산을 수행
    - 데이터 무결성 보장 필요
        - Reader들은 동시에 데이터 접근 가능
        - Writer들(또는 reader와 writer)이 동시 데이터 접근시, 상호배제(동기화) 필요
    - 해결법
        - Reader / writer 에 대한 우선권 부여
            - Reader preference solution
            - Writer preference solution 
- Dining philosopher problem
- 기타 

Semaphore Special Point 
- No busy waiting 
    - 기다려야 하는 프로세스는 block(asleep)상태가 됨 
- Semaphore queue에 대한 wake-up 순서는 비결정적
    - Starvation problem (운이 없는 프로세스는 계속 자게 된다) 
    - 생산자가 생산을 하고 놓으려고 할 때 누군가 생산된 것을 가져가면 안 되고 

![스크린샷 2023-02-20 오후 3 39 15](https://user-images.githubusercontent.com/60722292/220036284-d2af9acc-4417-4578-af29-6fd883d07b10.png)
![스크린샷 2023-02-20 오후 3 39 04](https://user-images.githubusercontent.com/60722292/220036307-d901c26b-99eb-47a1-9d51-640e94095935.png)
![스크린샷 2023-02-20 오후 3 38 54](https://user-images.githubusercontent.com/60722292/220036319-bcfc35de-49f8-4371-a44c-2268c7c0e54d.png)


