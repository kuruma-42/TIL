# Main Memory Management 
- register, cache H/W가 관리
- 메인메모리, 보조기억장치 S/W가 관리 

Block 
- 보조기억장치와 주기억장치 사이의 데이터 전송 단위 
- Size: 1-4kb

Word 
- 주기억장치와 레지스터 사이의 데이터 전송 단위
- Size: 16 - 64 bits 

Address Binding 
- 프로그램의 논리 주소를 실제 메모리의 물리 주소로 매핑하는 작업

Binding 시점에 따른 구분 
- Compile time binding 
- Load time binding 
- Runt time binding 


Complie time binding 
- 프로세스가 메모리에 적재될 위치를 컴파일러가 알 수 있는 경우
    - 위치가 변하지 않음
- 프로그램 전체가 메모리에 올라가야함 

Load time binding (중요) 
- 메모리 적재 위치를 컴파일 시점에서 모르면, 대체 가능한 상대 주소를 생성
- 적재 시점(load time)에 시작 주소를 반영하여 사용자 코드 상의 주소를 재설정 
- 프로그램 전체가 메모리에 올라가야 함 
- Logical address 240  Allocation address = 400 Reloacation 하면 640이 된다. 

Run time binding (중요) 
- Address binding을 수행시간까지 연기
    - 프로세스가 수행 도중 다른 메모리 위치로 이동할 수 있음 
- HW의 도움이 필요 
    - MMU: Memory Management Unit 
- 대부분의 OS가 사용 

Dynamic Loading 
- 모든 루틴을 교체 가능한 형태로 디스크에 저장
- 실제 호출 전 까지는 루틴을 적재하지 않음 
    - 메인 프로그램만 메모리에 적재하여 수행
    - 루틴의 호출 시점에 address binding 수행
- 장점 : 메모리 공간의 효율적 사용 

Swapping 
- 프로세서 할당이 끝나고 수행 완료 된 프로세스는 Swap-device로 보내고(Swap Out) 
- 새롭게 시작하는 프로세스는 메모리에 적재 (Swap In) 

Memory Allocation 
- Continous Memory Allocation(연속 할당) 
    - Uni-Programming
    - Multi-Programming
        - Fixed Partition(FPM)
        - Variable Partition(VPM) 

Continuous Memory Allocation 
- 프로세스(context)를 하나의 연속된 메모리 공간에 할당하는 정책
    - 프로그램 데이터 스택 등 
- 메모리 구성 정책
    - 메모리에 동시에 올라갈 수 있는 프로세스의 수 
        - MultiProgramming degree
    - 각 프로세스에게 할당되는 메모리 공간 크기 
    - 메모리 분할 방법 

Uni-Programming 
- Multiprogramming degree = 1 
- 한 번에 한 개만 하는 프로그램 

Multi-programming 
- Fixed(Static) partition multi-programming (FPM)
    - 고정 분할
- Variable(dynamic) partition multi-programming(VPM)

Uni-Programming 
- 문제점
    - 프로그램의 크기 > 메모리 크기
    - 커널 보호
    - Low System Resource Utilization 
    - Low System Performance 
- 해결법
    - Overlay Structure
        - 메모리에 현재 필요한 영역만 적재
        - 사용자가 프로그램의 흐름 및 자료구조를 모두 알고있어야 함(피로감 존재)
    - 경계 레지스터 사용 
    - Multi-programming 

Fixed Partition Multiprogramming 
- 메모리 공간을 고정된 크기로 분할
    - 미리 분할되어있음 
- 각 프로세스는 하나의 partition(분할)에 적재
- partition의 수 = k
    - multiprogramming degree = k 

Fragmentation (단편화)
- Internal fragmentation
    - 내부 단편화
    - Partition의 크기 > Process 크기
        - 메모리가 낭비됨 

- External fragmentation
    - 외부 단편화 
    - (남은 메모리 크기 > Process 크기지만, 연속된 공간이 아님) 
    - 메모리가 낭비 됨 

Summary 
- 고정된 크기로 메모리 미리 분할
- 메모리 관리가 간편함
    - Low overhead 
- 시스템 자원이 낭비 될 수 있음
- Internal/ external fragmentation 

Variable Partition Multiprogramming 
- 초기에는 전체가 하나의 영역
- 프로세스를 처리하는 과정에서 메모리 공간이 동적으로 분할
- No internal fragmentation 

배치 전략
- First fit (최초적합)
    - 충분한 크기를 가진 첫 번째 partition을 선택
    - Simple and low overhead 
    - 공간 활용률이 떨어질 수 있음 
- Best fit (최적적합)
    - Process가 들어갈 수 있는 Partition 중 가장 작은 곳 선택
    - 탐색 시간이 오래 걸림
        - 모든 Partition을 살펴봐야 함
    - 크기가 큰 Partition을 유지 할 수 있음
    - 작은 크기의 partition이 많이 발생
        - 활용하기 너무 작은
- Worst fit(최악 적합)
    - Process가 들어갈 수 있는 partition 중 가장 큰 곳을 선택
    - 탐색 시간이 오래 걸림
        - 모든 partition을 살펴봐야 함 
    - 작은 크기의 partition 발생을 줄일 수 있음 
    - 큰 크기의 partitionon 확보가 어려움
        - 큰 프로세스에게 필요한
- Next fit(순차 최초 적합) 
    - 최초 적합 전략과 유사
    - State table에서 마지막으로 탐색한 위치부터 탐색
    - 메모리 영역의 사용 빈도 균등화
    - Low overhead 

Coalescing holes(공간 통합)
- 인접한 빈 영역을 하나의 Partition으로 통합 
    - process가 memory를 release하고 나가면 수행
    - Low overhead 

Storage Compaction (메모리 압축)
- 모든 빈 공간을 하나로 통합
- 프로세스 처리에 필요한 적재 공간 확보가 필요할 때 수행
- High overhead 
    - 모든 Process재배치(Process 중지)
    - 많은 시스템 자원을 소비 

Summary of Continuous Memory Allocation 
- Uni Programming 
    - Simple
    - Fragmentation proble
- Fixed Partition Multi-Programming (FPM)
- Variable Partition Multi-Prgramming (VPM)
    - placement strategies
        - first-fit, best-fit, worst-fit, next-fit
    - External Fragmentation Issue 
        - Coalescing holes 
        - Storage Compaction 
