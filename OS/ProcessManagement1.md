# Process Management1

Job vs Process 

- 작업(Job) / 프로그램 (Program)
    - 실행 할 프로그램 + 데이터 
    - 컴퓨터 시스템에 실행 요청 전의 상태 

- 프로세스 (Process)
    - 실행을 위해 시스템(커널)에 등록된 작업
    - 시스템 성능 향상을 위해 커널에 의해 관리 됨 
    - 커널에서 프로세스를 관리하는 이유는 당연히 시스템의 성능을 향상시키기 위함.
- 프로세스의 정의
    - 실행중인 프로그램
        - 커널에 등록되고 커널의 관리하에 있는 작업
        - 각종 자원들을 요청하고 할당 받을 수 있는 개체 
        - 프로세스 관리 블록(PCB)을 할당 받은 개체
        - 능동적인 개체 (active entity)
            - 실행 중에 각종 자원을 요구, 할당, 반납하며 진행

    - Process Control Block (PCB)
        - 커널 공간 (kernel space) 내에 존재
        - 각 프로세스들에 대한 정보를 관리 

자원(Resource)의 개념
- 커널의 관리 하에 프로세스에게 할당/반납 되는 수동적 개체 (passive entity)
- 할당/ 반납은 커널이 관리한다.
- 자원의 분류 
    - H/W resources
        - Processor, memory, disk, monitor, keyboard, Etc.
    - S/W resources
        - Message, signal, files, installed SWs, Etc.

Process Control Block (PCB)
- 프로세스를 컨트롤 하기위해 모아놓은 블럭
- OS가 프로세스 관리에 필요한 정보 저장
- 프로세스 생성 시, 생성 됨 
- 커널이 관리하는 영역에 저장이 됨 

PCB가 관리하는 정보
- PID : Process Identification Number
    - 프로세스 고유 식별 번호
- 스케줄링 정보
    - 프로세스 우선순위 등과 같은 스케줄링 관련 정보들
- 프로세스 상태
    - 자원 할당, 요청 정보 등
- 메모리 관리 정보
    - Page table, segment table 
- 입출력 상태 정보
    - 할당 방은 입출력 장치, 파일 등에 대한 정보 등
- 문맥 저장 영역(context save area)
    - 프로세스의 레지스터 상태를 저장하는 공간 등
- 계정 정보
    - 자원 사용 시간 등을 관리
    - 다중 사용자 시스템의 경우

* PCB 정보는 OS 별로 서로 다름
* PCB 참조 및 갱신 속도는 OS의 성능을 결정 짓는 중요한 요소 중 하나

프로세스의 상태 (Process States)
* 프로세스 - 자원 간의 상호작용에 의해 결정
* 프로세스 상태 및 특성
<img width="593" alt="Running" src="https://user-images.githubusercontent.com/60722292/182534890-94e2f910-389a-4aa6-bc9f-26889b391e48.png">

Created State
* 작업(Job)을 커널에 등록 
* PCB 할당 및 프로세스 생성
* 커널
    * 가용 메모리 공간 체크 및 프로세스 상태 전이 
    * Ready or Suspended ready
    * (메모리가 있다면 Ready State, 메모리가 없다면 Suspended Ready)
<img width="442" alt="allocated" src="https://user-images.githubusercontent.com/60722292/182535001-08a8c35b-a462-4431-841d-b1c743541f67.png">

Ready State
* 프로세서 외에 다른 모든 자원을 할당 받은 상태
    * 프로세서 할당 대기 상태
    * 즉시 실행 가능 상태
* Dispatch(or Schedule)
    * Ready State -> Running State 
    * CPU를 할당 받으면 Running 상태로 바뀌게 되는데 이를 Dispatch되었다, 
    * 스케줄 되었다 라고 얘기한다. 

Running State
* 프로세서와 필요한 자원을 모두 할당 받은 상태
* Preemption
    * Running state -> reday states
    * 프로세서 스케줄링 (e.g, time-out, priorty changes)
    * (프로세서를 뺏겨나서 Ready로 내려간 상태)
* Block/ Sleep
    * Running State -> Asleep State 
    * I/O 등 자원 할당 요청

Blocked/ Asleep State
* 프로세서 외에 다른 자원을 기다리는 상태
    * 자원 할당은 System call에 의해 이루어 짐
* Wake-up
    * Asleep state -> Ready State
    * asleep에서 바로 running으로는 정책에 따라 다르겠지만 대부분 갈 수 없다.
    * 다른 Running Process가 끝나기를 기다린 후( Ready State ) 다시 작업을 수행한다.

<img width="457" alt="dispatch" src="https://user-images.githubusercontent.com/60722292/182535138-fc2f23b1-be34-48d1-a548-7a689cf2a608.png">

Suspended State
* 메모리를 할당 받지 못한 (빼앗긴) 상태
    * Memory image를 Swap Device에 보관
        * Swap Device: 프로그램 정보 저장을 위한 특별한 파일 시스템
    * 커널 또는 사용자에 의해 발생
* Swap-out(suspended), Swap-in(resume)
* Suspended란 memory도 없는 상태라고 생각하면 된다
* 메모리를 뺏기면서 Swap Device에 메모리 정보를 저장하는 것을 Swap Out이라고 한다
* 다시 메모리를 할당 받으면 Swap Device에 있는 메모리 정보를 꺼내는 것을 Swap In이라 한다.

Terminated/ Zombie State 
* 프로세스 수행이 끝난 상태
* 모든 자원 반납 후,
* 커널 내에 일부 PCB 정보만 남아있는 상태
    * 이후 프로세스 관리를 위해 정보 수집
* (커널이 PCB의 정보(어떤 자원을 요청했는지, 어떤 프로세스를 했는지)를 수집하기 위해 거쳐가는 State)

프로세스 관리를 위한 자료구조
* Ready Queue
* I/O Queue
* Device Queue
