# 운영체제의 구조
- 커널(Kernel)
- OS의 핵심 부분 (메모리 상주)
    - 가장 빈번하게 사용되는 기능들 담당
        - 시스템 관리(processor, memory, Etc) 등
    - 동의어
        - 핵, 관리자 프로그램, 상주 프로그램, 제어 프로그램
        - neucleus, supervisor, resident program, control program
- 유틸리티(Utility)
    - 비상주 프로그램
    - UI 등 서비스 프로그램
<br>
<img width="677" alt="스크린샷 2022-06-06 오후 8 18 53" src="https://user-images.githubusercontent.com/60722292/172153528-15ed17ab-bcce-4a18-938e-0487170bfe51.png">


단일 구조 
<br>
<img width="726" alt="스크린샷 2022-06-06 오후 8 20 17" src="https://user-images.githubusercontent.com/60722292/172153667-828d6dc2-9a4c-4835-ad09-80db599964c9.png">

- 장점 
    - 커널 내 모듈간 직접 통신
        - 효율적 자원 관리 및 사용
- 단점
    - 커널의 거대화
        - 오류 및 버그, 추가 기능 구현 등 유지보수가 어려움
        - 동일 메모리에 모든 기능이 있어, 한 모듈의 문제가 전체 시스템에 영향
        - ( 예, 악성 코드 등)

계층 구조 
<br>
<img width="614" alt="스크린샷 2022-06-06 오후 8 24 24" src="https://user-images.githubusercontent.com/60722292/172153768-f9d83e87-d7b5-4f4a-8737-da03673ca309.png">
- 장점
    - 모듈화
        - 계층간 검증 및 수정 용의
    - 설계 및 구현의 단순화
- 단점
    - 단일구조 대비 성능 저하
        - 원하는 기능 수행을 위해 여러 계층을 거쳐야 함

마이크로 커널 구조 
￼

- 커널의 크기 최소화
    - 필수 기능만 포함
    - 기타 기능은 사용자 영역에서 수행

Summary
운영체제의 기능
- 프로세스 관리
- 프로세서 관리
- 메모리 관리
- 파일 관리
- 입출력 관리
- 보조 기억 장치 및 기타 주변장치 관리 등

Process ManageMent
- 프로세스
    - 커널에 등록된 실행 단위(실행 중인 프로그램)
    - 사용자 요청/프로그램의 수행 주체(entity)
- OS의 프로세스 관리 기능
    - 생성/삭제, 상태 관리
    - 자원할당
    - 프로세스 간 통신 및 동기화(synchronization)
    - 교착상태(deadlock)해결
- 프로세스 정보 관리
    - PCB(Process Control Block)

- 중앙 처리 장치(CPU) (프로세서 큰 그림에서)
    - 프로그램을 실행하는 핵심 자원
- 프로세스 스케쥴링
    - 시스템 내의 프로세스 처리 순서 결정
- 프로세서 할당 관리
    - 프로세스들에 대한 프로세서 할당
        - 한 번에 하나의 프로세스만 사용 가능

Memory ManageMent
- 주기억장치
    - 작업을 위한 프로그램 및 데이터를 올려 놓는 공간
- Multi-user, Multi-tasking 시스템
    - 프로세스에 대한 메모리 할당 및 회수
    - 메모리 여유 공간 관리
    - 각 프로세스의 할당 메모리 영역 접근 보호
- 메모리 할당 방법(scheme)
    - 전체 적재
        - 장점: 구현이 간단/ 단점: 제한적 공간
    - 일부 적재 (Virtual Memory Concenpt)
        - 프로그램 및 데이터의 일부만 적재
        - 장점: 메모리의 효율적 활용 / 단점: 보조기억 장치 접근 필요

File ManageMent
- 파일 : 논리적 데이터 저장 단위

- 사용자 및 시스템의 파일 관리
- 디렉토리 구조 지원
- 파일 관리 기능
    - 파일 및 디렉토리 생성/삭제
    - 파일 접근 및 조작
    - 파일을 물리적 저장 공간으로 사상(mapping)
    - 백업 등

I/O ManageMent
- 입출력(I/O)과정 
    - OS를 반드시 커쳐야 함

Others
- Disk
- Networking
- Security and Protection System
- Command interpretor System
- System Call Interface
    - 응용 프로그램과 os 사이의 인터페이스
    - os가 응용프로그램에 제공하는 서비스 



