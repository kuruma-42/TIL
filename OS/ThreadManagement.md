# Thread Management 
<img width="421" alt="(resources)" src="https://user-images.githubusercontent.com/60722292/182763650-77a11d36-5347-40ba-b99a-1b2ccbc7e0b5.png">

- 하나의 프로세스 안에 여러 개의 스레드가 있을 수 있다
- 하나의 프로세스 안에 여러 개의 제어 할 수 있다. 

<img width="540" alt="스크린샷 2022-08-04 오전 11 32 46" src="https://user-images.githubusercontent.com/60722292/182763685-be975133-3039-4b6f-87bc-cee78a86e5dc.png">

- 프로세스가 할당 받은 리소스는  공유한다
- 자원을 제어하는 Thread는 여러 개가 있을 수 있다. 

<img width="609" alt="스크린샷 2022-08-04 오후 12 38 46" src="https://user-images.githubusercontent.com/60722292/182763733-fbdc3c37-a48b-4bf5-9654-8038cd489a44.png">

스레드 (Thread )
* Light Weight Process (LWP)
* 프로세서 (e.g, CPU)활용의 기본 단위
* 구성요소
    * Thread ID
    * Register set (PC<program counter>, SP<stack pointer> 등)
    * Stack (i.e local data) *작업 영역
* 제어 요소 외 코드, 데이터 및 자원들은 프로세스 내 다른 스레드들과 공유
* 전통적 프로세스 = 단일 스레드 프로세스
  
  <img width="541" alt="Single-thread vs Multi-threads" src="https://user-images.githubusercontent.com/60722292/182763757-c9319a4e-6f2d-4578-8b15-ed2239b2dd1a.png">

스레드의 장점
* 사용자 응답성(Responsiveness)
    * 일부 스레드의 처리가 지연되어도, 다른 스레드는 작업을 계속 처리 가능
* 자원 공유 (Resource sharing)
    * 자원을 공유해서 효율성 증가 (커널의 개입을 피할 수 있음)
        * ex) 동일 address space에서 스레드 여러 개 
        * P1,P2는 자원을 번갈아가며 자원을 사용하지만( context switch ) 
        * T1,T2는 자원을 같이 사용하더라도 context switch는 발생하지 않기 때문에 효율적이다.
* 경제성 (Economy)
    * 프로세스의 생성, context switch에 비해 효율적
* 멀티 프로세서(multi-processor)활용
    * 병렬처리를 통해 성능 향상

  <img width="559" alt="스크린샷 2022-08-04 오후 12 59 43" src="https://user-images.githubusercontent.com/60722292/182763784-ab86ef5a-3c72-4830-8b31-98ebe8137b0c.png">

- 단일 스레드의 예
- 마우스 클릭이나 스피커에서 IO가 발생한다. 
- IO가 발생하면 Run 에서 Block State가 되며, 프로세서가 다시 Ready로 갔다가 Run으로 가는 현상이 발생한다
- 단일 스레드에서는 화면이 나오는 중간에 마우스를 돌리면 순간 화면이 멈추고 마우스가 반응하고 다시 화면이 나오는 현상이 벌어질 것이다
- 마찬 가지로 소리가 나오면 화면이 멈추고 소리가 멈추면 다시 화면이 움직일 것이다
- 결과적으로 게임을 할 수 없다

* 스레드를 3개 발생시킨다
* 마우스 스피커 모니터의 작업을 같이 하게 만든다 
* 결과적으로 ‘사용자 응답성 (Responsiveness)를 높일 수 있다

스레드의 구현
* 사용자 수준 스레드 (User thread)
* 커널 수준 스레드 (Kernel thread)

사용자 수준 스레드 (User Thread)
* 사용자 영역의 스레드 라이브러리로 구현 됨
    * 스레드의 생성, 스케줄링 등
    * POSIX threads, Win32 threads, java thread API 등
* 커널은 스레드의 존재를 모름
    * 커널의 관리(개입)를 받지 않음
        * 생성 및 관리의 부하가 적음, 유연한 관리 가능
        * 이식성(portability)이 높음
    * 커널은 프로세스 단위로 자원 할당
        * 하나의 스레드가 block 상태가 되면, 모든 스레드가 대기
        * (Single Thread Kernel의 경우) 
  
  <img width="541" alt="스크린샷 2022-08-04 오후 1 11 14" src="https://user-images.githubusercontent.com/60722292/182763817-60a174ce-7eee-4012-8ff2-0ce3e7249163.png">

- 사용자 수준의 스레드는 여러 개 인데 
- 커널 수준의 스레드는 하나이다
- 다대일 (n:1) 매핑이 된다.

커널 수준 스레드 (Kernel Threads)
* OS(Kernel)가 직접 관리
* 커널 영역에서 스레드의 생성, 관리 수행
    * Context switching 등 부하(Overhead)가 큼
* 커널이 각 스레드를 개별적으로 관리
    * 프로세스 내 스레드들이 병행 수행 가능
        * 하나의 스레드가 block 상태가 되어도, 다른 스레드는 계속 작업 수행 가능
  
  
  
  <img width="490" alt="스크린샷 2022-08-04 오후 1 19 56" src="https://user-images.githubusercontent.com/60722292/182763933-f00d2973-bf42-4b90-a5f4-f12fcb45a96b.png">

  <img width="609" alt="Multi-Threading Model" src="https://user-images.githubusercontent.com/60722292/182764025-d4525654-504c-48d2-a2b1-c33d4868a282.png">

혼합형 (n:m) 스레드
* n개 사용자 수준 스레드 - m개의 커널 스레드 (n>m)
* 사용자는 원하는 수만 큼 스레드 사용
* 커널 스레드는 자신에게 할당된 하나의 사용자 스레드가 block 상태가 되어도,
* 다른 스레드 수행 가능
    * 병행 처리 가능
* 효율적이면서도 유연함

  <img width="499" alt="스크린샷 2022-08-04 오후 1 27 41" src="https://user-images.githubusercontent.com/60722292/182764068-323021d7-1359-4232-adce-b8d787138c4f.png">

Summary
스레드(Thread)의 개념
* 자원은 공유하지만 자신만의 제어요소를 가지고 있는 것 
* 자원을 공유하니깐 작업을 효율적으로 할 수 있다
* 여러 개의 자원을 동시에 사용할 수 있으면서, 병렬처리가 가능하다
  
  
  
  
  
  
