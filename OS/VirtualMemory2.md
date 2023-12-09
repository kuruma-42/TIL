# Virtual Memory

Segmentation System 
- 프로그램을 논리적 block으로 분할 (segment) 
    - Block의 크기가 서로 다를 수 있음 
    - ex) stack, heap, main procedure, shared lib, etc 
- 특징
    - 메모리를 미리 분할 하지 않음
        - VPM
    - Segment Sharing/ Protection이 용이함 
    - Address mapping 및 메모리 관리의 overhead가 큼
    - No internal fragmentation
        - External fragmentation 발생 가능 

- Address mapping 
    - Virtual Address: v = (s, d) 
        - s: segment number
        - d: displacement in a segment 
    - Segment Map Table (SMT)
    - Address Mapping Mechanism 
        - paging system과 유사 

- Segment map Table (SMT) 
    - VPM과 유사하다 
    - segment length column, protection bits(R/W/X/A)<Process의 권한> column 존재

Address Mapping(direct mapping)
- 프로세스의 SMT가 저장되어 있는 주소 b에 접근
- SMT에서 segment s의 entry찾음
    - s의 entry위치 = b + s * entrySize  
- 찾아진 Entry에 대해 다음 단계들을 순차적으로 실행
    - 존재 비트가 0 인 경우, // missing segment fault  swap device로 부터 해당 segment를 메모리로 적재 SMT를 갱신
    - 변위 (d)가 segment 길이보다 큰 경우 (d > ls) (segment overflow exception 처리 모듈을 호출) 
    - 허가되지 않은 연산일 경우 (protection bit filed 검사),  (segment protection exception) 처리 모듈을 호출
- 실제 주소 r 계산 (r = as + d)
- r로 메모리에 접근 

Memory Management
- VPM과 유사
    - segment 적재 시, 크기에 맞추어 분할 후 적재 

Segment sharing/ protection 
    - 논리적으로 분할되어 있어, 공유 및 보호가 용이함 

Segmentation System Summary 
- 프로그램을 논리 단위로 분할(segment) / 메모리를 동적으로 분할
    - 내부 단편화 문제 없음
    - Segment sharing/ protection이 용이함
    - Paging System 대비 관리 overhead가 큼 
- 필요한 segment만 메모리에 적재하여 사용
    - 메모리의 효율적 활용
- Segment mapping overhead
    - 메모리 공간 및 추가적인 메모리 접근이 필요
    - 전용 HW활용으로 해결 가능 

Paging VS Segmentation 
- Paging system
    - simple low overhead
    - No logical concept for partitioning
    - Complex page sharing mechanism ( logical하게 안 나눠놔서 공유나 보호가 어렵다 ) 
- Segmentation System 
    - High Management overhead (논리적으로 자르기 때문에 관리의 overhead가 크다)
    - Logical concept for partitioning 
    - Simple and easy sharing mechanism ( logical하게 나눠놔서 공유, 보호가 쉽다) 
