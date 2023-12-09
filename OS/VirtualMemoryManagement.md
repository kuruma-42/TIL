# Virtual Memory Management 
- 가상 메모리 관리의 목적
    - 가상 메모리 시스템 성능 최적화
        - Cost model
        - 다양한 최적화 기법

Cost Model for Virtual Mem. Sys.
- Page fault frequency (발생 빈도)
- Page fault rate (발생률) 
- Page fault rate를 최소화 할 수 있도록 전략들을 설계해야 함 
    - Context Switch 및 Kernel 개입을 최소화 
    - 시스템 성능 향상 

- Page reference string(d)
    - 프로세스의 수행 중 참조한 페이지 번호 순서
    - w = r1, r2, …rk, … rt
        - ri = 페이지 번호 
        - N: 프로세스 페이지 수 ( 0 ~ N - 1 ) 
- Page fault rate = F(w) 
    - F(w) = Num of page faults during w / |w
    - F(w) = page fault 수 / 참조한 전체 페이지 수 

- Hardware componets
    - 주소 사상을 효율적으로 수행하기 위해 사용 
        - ex) TLB(associated memories), Dedicated page-table register, Cache memories 
    - Bit Vectors 
        - Page 사용 상황에 대한 정보를 기록하는 비트들
        - Reference bits (used bit) 
            - 참조 비트 
        - Update bits (modified bits, write bits, dirty bits)
            - 갱신 비트 
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




