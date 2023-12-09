
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
