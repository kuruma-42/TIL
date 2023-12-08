# Non-continous allocation / Virtual memory 
- Non-continous allocation
- 사용자 프로그램을 여러 개의 block으로 분할
- 실행 시, 필요한 block들만 메모리에 적재
    - 나머지 block들은 swap device에 존재

Methods
- Paging System
- Segmentation System
- Hybrid paging/ segmentation system 

Address Mapping
- Continous Allocation
    - Relative Address(상대 주소)
        - 프로그램의 시작 주소를 0으로 가정한 주소 
    - Relocation 
        - 메모리 할당 후, 할당된 주소에 다라 주소들을 조정하는 작업 

Non-continous Allocation 
- Virtual (가상주소) = relative address
    - Logical address (논리주소)
    - 연속된 메모리 할당을 가정한 주소
- Real Address (실제주소) = absolute(physical)
    - 실제 메모리에 적재된 주소
- Address mapping 
    - Virtual Address -> Real Address 
- * 사용자/프로세스는 실행 프로그램 전체가 메모리에 연속적으로  적재되었따고 가정하고 실행할 수 있음 

Block Mapping 
- 사용자 프로그램을 block 단위로 분할/관리
    - 각 block에 대한 address mapping 정보 유지
- Virtual address: v = (b,d)
    - b = block number
    - d = displacement(offset) in a block (b에서부터 얼마나 떨어져있는가) 

Block Map Table (BMT) 
- Address mapping 정보 관리 
    - Kernel 공간에 프로세스마다 하나의 BMT를 가짐 
    - Residence bit: 해당 블록이 메모리에 적재되었는지 여부 

Block Mapping 
- 프로세스의 BMT에 접근 
- BMT에서 block d에 대한 항목(entry)를 찾음 
- Residence bit 검사 
    - Residence bit = 0의 경우 
        - Swap Device에서 해당 블록을 메모리로 가져 옴 
        - BMT 업데이트 후 Residence bit가 있는 경우의 단계 수행
    - Residence bit = 1의 경우,
        - BMT에서 b에 대한 Real Address 값 a확인 
- 실제 주소 r 계산 ( r = a + d )
- r을 이용하여 메모리에 접근 

Paging System (중요) 
- 프로그램을 같은 크기의 블록으로 분할 (pages) 
- page = 프로그램의 분할된 block 
- page frame 
    - 메모리의 분할 영역
    - page와 같은 크기로 분할 
- 특징 
    - 논리적 분할이 아님 (크기에 따른 분할)
        - Page 공유(Sharing) 및 보호(Protection) 과정이 복잡함
            - Segmentation 대비
    - Simple and Efficient
        - Segmentation 대비 
    - No external fragmentation
        - Internal gragmentation 발생 가능 

Address Mapping 
- Virtual Address: v = (p,d)
    - p: page number 
    - d: displacement(offset)
- Address Mapping 
    - PMT(Page Map Table) 사용
- Address Mapping Mechanism 
    - Direct Mapping(직접 사상)
    - Associative mapping(여관 사상) 
        - TLB(Translation Look-aside Buffer)
    - Hybrid direct/ associative mapping 

Dircet Mapping
- Block Mapping 방법과 유사 
- PMT에는 Page number, Secondary Storage address, page frame number등이 들어간다
- 가정
    - PMT를 커널 안에 저장 
    - PMT entry size = entrySize 
    - Page size = pageSize

Direct Mapping Process 
- 해당 프로세스의 PMT가 저장되어 있는 주소 b에 접근
- 해당 PMT에서 page p에 대한 entry를 찾음
    - p의 entry 위치 = b + p * entrySize 
- 찾아진 entry의 존재 비트 검사 
    - Residence bit = 0 인 경우 (page fault), Swap Device에서 해당 Page를 메모리로 적재  PMT를 갱신한 후 3-2 단계 수행 
    - Residence bit = 1 인 경우 해당 entry에서 page frame 번호 p’fmf ghkrdls 
- pf와 가상 주소의 변위 d를 사용하여 실제 주소 r 형성
- r = p’* pageSize + d 
- 실제 주소 r로 주기억장치에 접근 

Direct Mapping 
- 문제점 
    - 메모리 접근 횟수가 2배
        - 성능 저하
    - PMT를 위한 메모리 공간 필요 
- 해결방안
    - Associative Mapping(TLB)
    - PMT를 위한 전용 기억장치(공간) 사용
        - Dedicated register or cache memory 
    - Hierarchical paging
    - Hashed page table
    - Inverted page table 

Associative Mapping 
- TLB(Translation Look-aside Buffer)에 PMT적재 
    - Associative High-Speed Memory (전용 하드웨어)
- PMT를 병렬 탐색 
- Low overhead, High speed 
- Expensive Hardware 
    - 큰 PMT를 다루기가 어려움 


