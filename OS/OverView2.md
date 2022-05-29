# OS OverView chapter2

#### 운영체제의 역할
- User Interface(편리성)
    - CUI(Character user interface)
    - GUI(Graphical user interface)
    - EUCI(End-User Comfotable Interface)
- Resource management(효율성)
    - HW resource(processor, memory, I/O devices, Etc)
    - SW resource(file, application, message, signal, Etc.)
- Process and Thread Management
- System management(시스템 보호)

#### 컴퓨터 시스템의 구성
<br>
<img width="583" alt="Multi-layer architecture" src="https://user-images.githubusercontent.com/60722292/170865755-2542e601-13b2-40ed-9448-d7ddf5b45b29.png">


#### 운영체제의 구분
- 동시 사용자 수
    - Single-user system
    - Multi-user system
- 동시 실행 프로세스 수 
    - Single-tasking system
    - Multi-tasking system (Multiprogramming system)
- 작업 수행 방식 (사용자가 느끼는 사용 환경)
    - Batch processing system
    - Time-sharing system
    - Distributed processing system
    - Real-time system

#### 동시 사용자 수 
- 단일 사용자 (single-user system)
    - 한 명의 사용자만 시스템 사용가능
        - 한 명의 사용자가 모든 시스템 자원 독점
        - 자원관리 및 시스템 보호 방식이 간단 함
    - 개인용 장비 등에 사용
        - windows,android,iOS,MS-DOS
- 다중 사용자(Multi-user system)
    - 동시에 여러 사용자들이 시스템 사용
        - 각종 시스템 자원(파일 등)들에 대한 소유 권한 관리 필요
        - 기본적으로 Milti-tasking 기능 필요
        - os의 기능 및 구조가 복잡
    - 서버 클러스터(cluster) 장비 등에 사용
        - Unix, Linux, Window server 등

#### 동시 실행 프로세스 수 
- 단일작업(Single-tasking system)
    - 시스템 내에 하나의 작업(프로세스)만 존재
        - 하나의 프로그램 실행을 마친 뒤에 다른 프로그램의 실행
    - 운영체제의 구조가 간단
    - MS-DOS
- 다중작업(Multi-tasking system)
- 동시에 여러 작업(프로세스)의 수행 가능
    - 작업들 사이의 동시 수행, 동기화 등을 관리해야 함
- 운영체제의 기능 및 구조가 복잡
- 예) Unix/Linux, Window 등

