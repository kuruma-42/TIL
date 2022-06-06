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

#### 작업 수행 방식
- Batch processing system
    - 일괄 처리 시스템
- Time-Sharing system
    - 시분할 시스템
- Distributed processing system
    - 분산처리 시스템
- Real-time system
    - 실시간 시스템

#### 순차 처리 (No OS, ~ 1940s)
- 운영체제 개념 존재하지 않음
    - 사용자가 기계어로 직접 프로그램 작성
    - 컴퓨터에 필요한 모든 작업 프로그램에 포함
        - 프로세서에는 명령어 저장 방법, 계산 대상, 결과 저장 위치와 방법, 출력 시점, 위치 등
- 실행하는 작업 별 순차 처리
    - 각각의 작업에 대한 준비 시간이 소요

#### Batch System (1950s ~ 1960s)
- 모든 시스템을 중앙 (전자 계산소) 에서 관리 및 운영
- 사용자의 요청 작업(천공카드 등)을 일정 시간 모아두었다가 한 번에 처리
- 시스템 지향적 (system-oriented)

- 장점
    - 많은 사용자가 시스템 자원 공유
    - 처리 효율 향상
- 단점
    - 생산성 저하(productivity)
        - 같은 유형의 작업들이 모이기를 기다려야 함
        - 긴 응답시간(turnaround time)
            - 약 6시간(작업 제출에서 결과 출력까지의 시간)

#### Time Sharing System(1960s ~ 1970s)
- 여러 사용자가 자원을 동시에 사용
    - OS가 파일 시스템 및 가상 메모리 관리
- 사용자 지향적(User-oriented)
- 대화형(conversational, interactive)시스템
- 단말기(CRT terminal) 사용
- 장점 
    - 응답시간(response time) 단축 (약 5초)
    - 생산성(productivity) 향상
        - 프로세서 유휴 시간 감소
- 단점 
    - 통신 비용 증가
        - 통신선 비용, 보안 문제 등
    - 개인 사용자 체감 속도 저하
        - 동시 사용자 수 -> 시스템 부하 -> 느려짐(개인관점)

- Personal Computing
    - 개인이 시스템 전체 독점
    - CPU(활용률 uitilization)이 고려의 대상이 아님
    - OS가 상대적으로 단숨함
        - 하지만, 다양한 사용자 지원 기능 지원
        - 지원 기능(유저가 사용하기 편한 기능)
- 장점
    - 빠른 응답시간
- 단점
    - 성능(performance)이 낮음

#### Parallel Processing System
- 단일 시스템 내에서 둘 이상의 프로세서 사용
    - 동시에 둘 이상의 프로세스 지원
- 메모리 등의 자원 공유(Tightly-coupled system)
- 사용 목적
    - 성능 향상
    - 신뢰성 향상(하나가 고장 정상 동작 가능
- 프로세서간 관계 및 역할 관리 필요
- 

#### Distributed Processing Systems
- 네트워크를 기반으로 구축된 병렬처리 시스템
- (Loosely-coupled system)
    - 물리적인 분산, 통신망 이용한 상호 연결
    - 각각 운영체제 탑재한 다수의 범용 시스템으로 구성
    - 사용자는 분산운영체제를 통해 하나의 프로그램, 자원처럼 사용 가능
    - (은폐성, transparency)
    - 각 구성 요소들간의 독립성 유지, 공동작업 가능
    - Cluster system, client-server system, P2P 등

- 장점
    - 자원공유를 통한 높은 성능
    - 고신뢰성, 높은 확정성
- 단점
    - 구축 및 관리가 어려움

#### Real-time Systems
- 적업 처리에 제한 시간(deadline)을 갖는 시스템
    - 제한 시간 내에 서비스를 제공하는 것이 자원 활용 효율 보다 중요
- 작업의 종류
    - Hard real-time task
        - 시간 제약을 지키지 못하는 경우 시스템에 치명적 영향
        - 예, 발전소 제어, 무기 제어 등
        - Soft-real-time task
            - 동영상 재생 등
        - Non real-time task

