# Process Scheduling 1
다중프로그래밍 (Multi-programming) 
* 여러 개의 프로세스가 시스템 내 존재
* 자원을 할당 할 프로세스를 선택 해야 함
    * 스케줄링 (Scheduling)
* 자원 관리 
    * 시간 분할(time sharing) 관리
        * 하나의 자원을 여러 스레드들이 번갈아 가며 사용
        * 예) 프로세서 (Processor)
            * 프로세서 사용시간을 프로세스들에게 분배
        * 공간 분할 (space sharing) 관리
            * 하나의 자원을 분할하여 동시에 사용
            * 예) 메모리 (memory)

스케줄링(Scheduling)의 목적
* 시스템의 성능(performance)향상
* 대표적 시스템 성능 지표 (index)
    * 응답시간(response time)
        * 작업 요청(submission)으로부터 응답을 받을 때 까지의 시간
    * 작업 처리량(throughput)
        * 단위 시간 동안 완료된 작업의 수
    * 자원 활용도 (resource utilization)
        * 주어진 시간(Tc)동안 자원이 활용된 시간
* 목적에 맞는 지표를 고려하여 스케줄링 기법을 선택

시스템 성능 지표들
* 평균 응답 시간 (mean response time)
    * 사용자 지향적, 예) interactive systems 
* 처리량 (throughput)
* 자원 활용도 (resource utilization
* 공평성 (fairness)
    * FIFO
* 실행 대기 방지
    * 무기한 대기 방지
* 예측 가능성(predictability)
    * 적절한 시간 안에 응답을 보장하는가

<img width="486" alt="Waiting time" src="https://user-images.githubusercontent.com/60722292/183240443-af3daa46-1468-4a84-8d61-c6a4021bf5a0.png">

스케줄링 기준(Criteria)
* 스케줄링 기법이 고려하는 항목들
* 프로세스(process)의 특성
    * I/O-bounded or compute-bounded
* 시스템 특성
    * Batch system or interactive system
* 프로세스의 긴급성(urgency)
    * Hard- or Soft- realm time, non-real time systems
* 프로세스 우선순위 (priorty)
* 프로세스 총 실행 시간 (total service time) 
* …

CPU burst VS I/O burst
* 프로세스 수행
    * CPU 사용 + I/O 대기
* CPU burst
    * CPU 사용 시간 (연산에 의해서 성능이 좌우된다 Compute-bounded process)
* I/O burst
    * I/O 대기 시간 (I/O에 의해서 성능이 좌우될 때 I/O-bounded process)
* Burst time은 스케줄링의 중요한 기준 중 하나 

스케줄링의 단계 (Level) 
* 발생하는 빈도 및 할당 자원에 따른 구분
* Long-term scheduling
    * 장기 스케줄링
    * Job Scheduling
* Mid-term scheduling
    * 중기 스케줄링
    * Memory allocation
* Short-term scheduling
    * 단기 스케줄링
    * Process scheduling

Long-term Scheduling
* Job scheduling
    * 시스템에 제출 할 (Kernel에 등록 할) 작업(Job) 결정
        * Admission scheduling, High-level scheduling
* 다중프로그래밍 정도(degree) 조절
    * 시스템 내에 프로세스 수 조절
* I/O-bounded 와 Computed-bounded 프로세스들을 잘 섞어서 선택해야 함
    * why? 치우치게 쓰면 자원활용도가 떨어지고, 비효율적이다 
    * CPU, I/O를 적절히 섞어줘야 시스템의 효율이 올라간다. 
* 시분할 시스템에서는 모든 작업을 시스템에 등록
    * Long-term scheduling이 불필요
    * 시간을 나누어서 사용하기 때문에 몇 개가 들어와도 상관없다

Mid-term Scheduling
* 메모리 할당 결정(memory allocation)
    * intermediate-level scheduling
    * Swapping (swap-in/ swap-out)

Short-term Scheduling

<img width="219" alt="dispatch" src="https://user-images.githubusercontent.com/60722292/183240457-410c2c4f-dc51-4d3a-8e8f-142edf13c093.png">

* CPU를 할당해주는 Scheduling 
* Process Scheduling
    * Low-level scheduling
    * 프로세서(Processor)를 할당할 프로세스(Process)를 결정
        * Processor Scheduler, dispatcher
* 가장 빈번하게 발생
    * Interrupt, block (I/O), time-out, Etc.
    * 매우 빨라야 함
        * E.g.,
        * average CPU burst = 100ms
        * scheduling decision = 10ms
        * 10 x (100+10) = 9% of ther CPU is being used simply for scheduling

<img width="513" alt="Short-term" src="https://user-images.githubusercontent.com/60722292/183240469-cbe55e0f-da1f-4abb-b365-541d42f726e4.png">

스케줄링 정책 (Policy)
* 선점 vs 비선점
    * Preemptive scheduling, Non-preemptive scheduling
* 우선순위
    * priority

Preemptive(선점) / Non-preemptive scheduling
* Non-preemptive scheduling
    * 자원을 뺏기지 않는다.
    * 할당 받을 자원을 스스로 반납할 때 까지 사용
        * ex) system call, I/O, Etc.
    * 장점
        * Context switch overhead가 적음
    * 단점
        * 잦은 우선순위 역전, 평균 응답 시간 증가
* Preemptive scheduling
    * 타인에 의해 자원을 빼앗길 수 있음
        * 예) 할당 시간 종료, 우선순위가 높은 프로세스 등장
    * Context switch overhead가 큼
    * Time-sharing system, real-time system 등에 적합(응답성이 높아진다)

Priority
* 프로세스의 중요도
* Static Priority(정적 우선순위)
    * 프로세스 생성시 결정된 priorty가 유지 됨
    * 구현이 쉽고, overhead가 적음
    * 시스템 환경 변화에 대한 대응이 어려움
* Dynamic priorty (동적 우선순위)
    * 프로세스의 상태 변화에 따라 priorty 변경
    * 구현이 복잡, priorty 재계산 overhead가 큼
    * 시스템 환경 변화에 유연한 대응 가능

<img width="434" alt="Priority" src="https://user-images.githubusercontent.com/60722292/183240547-a080a54b-a4ab-48e2-a303-36c8fbe8bbd7.png">

Summary
* 멀티프로그래밍 (멀티테스킹)
* 스케줄링 개념
    * 목적
    * 성능 지표
        * CPU burst VS I/O burst
    * 스케줄링 기준 (Criteria)
* 스케줄링 레벨
    * Long-term, Mid-term, Short-term
* 스케줄링 정책
    * Preemptive/Non-preemptive
    * Priorty
