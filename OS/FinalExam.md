
# Final Exam 

1. 가상 메모리의 개념 및 필요성을 설명하고, 어떻게 구현하는지 대표적인 2가지 방식을 기술하시오 
- 개념 : 당장 실행해야 하는 부분만 주기억장치에 넣고 나머지는 보조기억장치에 넣어 동작하도록 하는 것 
- 2가지 방식: Demand paging, Demand Segmentation 
- paging은 일정한 크기의 page로 process를 분할하여 메모리에 올림 
- segmentation은 논리적으로 segment로 Process를 분할하여 메모리에 올림 


2. paging과 segmentation을 fragmentation 관점으로 논하라

paging  system 
- 프로세스를 같은 크기의 블록으로 분할한다. (pages) 
- 메모리의 분할 영역 (page frame) page와 같은 크기로 분할된다. 
- External Fragmentation은 발생하지 않는다.
- 분할된 블록의 크기가 고정되어 있어 Internal fragmentation이 발생한다. 

segmentation 
- 프로세스를 논리적 segment로 분할 
- 메모리를 미리 분할 하지 않는다. (block의 크기가 다를 수 있기 때문에 미리 못 자른다.)
- Internal Fragmentation이 발생하지 않는다. (요청 준 만큼 할당하기 때문에) 
    - External fragmentation 발생 가능 


3. address binding 3가지 방식 특징 
- compile time binding 
    - compile 할 때 address binding을 한다.
    - 프로세스가 메모리에 적재될 위치를 컴파일러가 알 수 있는 경우
        - 위치가 변하지 않음 (위치가 변경되었을 경우에는 반드시 다시 컴파일 해야한다.) 
- load time binding 
    - 메모리에 적재할 address binding을 한다. 
    - 메모리 적재 위치를 컴파일 시점에서 모르면, 대체 가능한 상대 주소를 생성 
- excution time binding 
    - 물리 주소가 실행시간에 결정됨. 
    - Run time binding이라고도 불림
    - Address binding을 수행시간 까지 연기 
    - 프로세스가 수행 도중 다른 메모리 위치로 이동할 수 있음 
    - HW의 도움이 필요
        - MMU: Memory Management Unit
    - 대부분의 OS가 사용 

4. 대표적인 3가지 페이지 교체 알고리즘 FIFO, Optimal, LRU방식에 대하여 프레임 수가 5일 때,  다음과 같은 수서로 페이지를 참조하는 경우 발생되는 Page Fault수를 각각 계산하시오 

<img width="584" alt="Pasted Graphic" src="https://github.com/kuruma-42/TIL/assets/60722292/5bcfb38c-036e-4cec-a8a9-8dee2e881dc7">

<br>

<img width="326" alt="Pasted Graphic 1" src="https://github.com/kuruma-42/TIL/assets/60722292/95122008-89f0-4f85-811b-4cecbfb43b32">

- FIFO 
    - 먼저 들어온 것을 먼저 내보내는 페이지 교체 알고리즘 
    - FIFO anomaly (Belady’s anomaly)
        - FIFO 알고리즘의 경우 더 많은 page frame을 할당 받음에도 불구하고 page fault의 수가 증가하는 경우가 있음
        - Locality를 고려하지 않아서 그렇다. 
- LRU (Least Recently Used) 
    - 가장 오랫동안 참조되지 않은 page를 교체
    - Page 참조 시 마다 시간을 기록해야 함 (Count)
    - Locality에 기반을 둔 교체 기법
    - MIN algorithm(Opt)에 근접한 성능을 보여줌
    - 실제로 가장 많이 활용되는 기법 
- MIN Algorithm (OPT algorithm) 
    - 앞으로 가장 오랫동안 참조되지 않을 page 교체 
    - 실현 불가능한 기법 
        - Page Reference String을 미리 알고 있어야 함 
* * Thrashing 
    * 과도한 page fault가 발생하는 현상 
    * 프로세스가 충분한 페이지가 없을 때 page-fault rate가 엄청 높다. 
        * CPU 사용률이 낮아지고
        * Multiprogramming Degree가 일정 수준 위로 올라가면  활발히 사용되는 페이지들만으로 이루어져 있으므로 어떤 페이지가 교체되던 바로 다시 페이지 교체가 필요하게 된다. 


5. 디렉토리 구조를 평가할 때 사용되는 3가지 기준에 따라, Single-level, Two-level, Tree 3종류의 디렉토리 구조를 비교하시오
- Single-Level Directory 
    - 모든 유저에게 디렉토리가 하나이기 때문에 이름 중복 X 
    - Grouping이 안 되는 문제 
- Two-Level Directory 
    - Path name: 경로명을 사용한다 User 레벨 부터 구분됨 (Searching에 효율적이다) 
    - 사용자 마다 하나의 directory 배정 
    - 다른 유저 간에 같은 파일 이름을 가질 수 있다. 
    - 효율 적인 검색 가능 (Linear Search를 해도 유저별로 검색 가능) 
    - No grouping capability => ( Ex: 게임, 프로그램 카테고리컬하게 구분이 안 된다) 
- Tree-Structed Directories (일반적으로 많이 씀) 
    - 검색이 효율적이다 (Grouping Search가 가능하다) 
    - Grouping 가능하다. 
    - 현재 위치를 관리해야한다. 
    - 사용자가 하부 directory 생성/ 관리 가능

6. 디스크 입출력 요청을 처리하기 위해서 사용되는 디스크 스케쥴링 방식에서 FCFS,SSTF,SCAN 3가시 방식에 대하여 전체 실린더 수가 100일 때, 처음 헤드가 51번에 위치해있고 다음과 같은 순서로 실린더를 요청하는 경우 헤드의 Seek 시간을 실린더 이동 수로 각각 계산하시오

￼<img width="728" alt="Pasted Graphic 2" src="https://github.com/kuruma-42/TIL/assets/60722292/5387a05a-8452-49ff-a35d-f3c7d4610d17">

<img width="345" alt="Pasted Graphic 3" src="https://github.com/kuruma-42/TIL/assets/60722292/cd3613d0-34ee-4166-8e73-27cf41a9f0fb">


7-2. TLB 
- Transition Look-aside Buffer 
- Paging을 할 때 메인메모리에 두 번 접근해서 생기는 비효율을 보완하기 위한 고성능 하드웨어
- 블록을 병렬로 검색하여 속도가 매우 빠르다.
- 비용이 비싸다. 
7-3. Acyclic-Graph Directories 
- Hierarchical Directory structure 확장 
- Directory 안에 Shared directory, shared file을 담을 수 있음 
- Link의 개념 사용 (바로가기 같이 연결해줌) 
* General Graph Directory 
    * Cycle을 허용
    * File 탐색 시, Infinite loop를 고려해야함
 

8. 디스크 할당 방식 
- Continous allocation 
    - 한 File을 디스크의 연속된 block에 저장
    - 장점 
        - 효율적인 file 접근 (순차, 직접 접근) 
    - 문제점 
        - 새로운 file을 위한 공간 확보가 어려움
        - External fragmentation 
        - File 공간 크기 결정이 어려움 
            - 파일이 커져야 하는 경우 고려해야 함.
- Discontinous allocation
    - Linked allocation
        - File이 저장된 block들을 linked list로 연결 
            - 비연속 할당 가능
        - Directory는 각 file에 대한 첫 번째 block에 대한 포인터를 가짐 
        - Simple, No external fragmentation 
        - 단점
            - 직접 접근에 비효율적
            - 포인터 저장을 위한 공간 필요
            - 신뢰성 문제
                - 사용자가 포인터를 실수로 건드리는 문제 등
    - Indexed allocation 
        - File이 저장된 block 정보를 Index blcok에 모아둠
        - 직접 접근에 효율적
            - 순차 접근에는 비효율적 
        - File당 Index블록을 유지
            - Space Overhead 
            - Index block 크기에 따라 파일의 최대 크기가 제한 됨 
        - UNIX 등에 사용됨 
        - 

--- 
기출 예상 문제 

9. I/O 메커니즘, 특히 DMA 중요 
- Processor controlled memory access (CPU가 제어한다) 
    - Polling (Programed I/O)
    - Interrupt 
- Direct Memory Access (DMA)(CPU가 관리하지 않음) 

Polling (Programmed I/O)
- 모든 I/O 장치를 순환하며 확인 
- 전송 준비 및 전송 상태 등 
- 장점
    - Simple 
    - I/O 장치가 빠르고 데이터 전송이 잦은 경우 효율적 
- 단점 
    - Processor의 부담이 큼
        - Polling overhead(I/O device가 느린 경우)

Interrupt 
- I/O 장치가 작업을 완료한 후, 자신의 상태를 Processor 에게 전달 
    - Interrupt 발생 시, Processor는 데이터 전송 수행
- 장점
    - Polling 대비 Low Overhead 
    - 불규칙적인 요청 처리에 적합
- 단점
    - Interrupt handling overhead 

Direct Memory Acess (DMA)
- Processor controlled memory access 방법 
    - Processor가 모든 데이터 전송을 처리해야 함
    - High overhead for the processor 
- Direct Memory Access 
    - I/O 장치와 Memory 사이의 데이터 전송을 Processor 개입 없이 수행 
- Processor는 데이터 전송의 시작/종료 만 관여
    1. 프로세서가 전송 방향, 전송 바이트 수, 데이터 블록의 메모리 주소 등을 DMA 제어기에 보낸다.
    2. DMA 제어기는 디스크 제어기에 데이터를 메인 메인 메모리로 전송하라고 요청한다. 
    3. 디스크 제어기가 메인 메모리에 데이터를 전송한다. (버퍼 존재) 
    4. 데이터 전송을 완료하면 디스크 제어기는 DMA 제어기에 완료 메시지를 전달한다.
    5. DMA 제어기가 프로세서에 인터럽트 신호를 보낸다. 

10. UNIX운영체제에서 각 파일에 대하여 데이터 블록이 디스크 상에서 어떠한 방식으로 할당되는지, 또한 inode구조를 통하여 어떻게 관리 되는지 설명하시오. 
- 유닉스가 대표적인 indexed allocation 방식 
- 싱글 인다이렉트 인덱스는 블록을 하나 거쳐서 데이터로 간다. 
- 더블 인다이렉트 인덱스는 블록을 두 개 거쳐 데이터로 간다. 
- 파일 사이즈가 클 때는 멀티레벨이 필요하다. 하나의 레벨로는 한계가 있다. 
- 하나의 블럭이 1k라고 가정하면 인덱스 블록이 10개면 최대 사이즈가 10k 
- Two-Level, Three-Level로 하면 파일을 훨씬 크게 쓸 수 있다. 
- 멀티레벨을 사용해서 대용량 파일을 사용할 수 있게 하고있음  

