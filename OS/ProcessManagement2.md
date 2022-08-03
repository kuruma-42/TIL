# Process Management2
인터럽트(Interrupt)
* 예상치 못한, 외부에서 발생한 이벤트
    * Unexpected, external events
* 인터럽트의 종류
    * I/O interrupt ( 베그할 때 총을 쏘려고 마우스를 클릭했을 때 )
    * Clock interrupt ( CPU가 일을 할 때 클락이 발생할 때 생김 )
    * Console interrupt ( Console에서 입력함 )
    * Program check interrupt  (프로그램에서 생김)
    * Machine check interrupt (하드웨어에서 문제가 있을 때 발생 )
    * Inter-process interrupt (다른 프로세스에 의해서 생김 )
    * System call interrupt 

인터럽트 처리 과정 
<img width="649" alt="Interrupt" src="https://user-images.githubusercontent.com/60722292/182560398-a832f518-2464-4760-a6b0-687f3d7113cb.png">
<img width="599" alt="Interrupt handling" src="https://user-images.githubusercontent.com/60722292/182560429-8c942a2a-cc64-46e2-b472-85603905f8d5.png">
Context Switching (문맥 교환)
* Context
    * 프로세스와 관련된 정보들의 집합
        * CPU Register context => in CPU
        * Code & Data, Stack, PCB => in memory 
* Context saving 
    * 현재 프로세스의 Register context를 저장하는 작업
* Context restoring 
    * Register context를 프로세스로 복구하는 작업 (CPU Register Context)
* Context switching
    * 실행 중인 프로세스 context를 저장하고,
    * 앞으로 실행 할 프로세스의 context를 복구 하는 일
        * 커널의 개입으로 이루어짐 
    * 상기의 Saving과 Restoring을 묶으면 Switching이 된다.

Context Switch Overhead
* Context Switching에 소요되는 비용
    * OS마다 다름
    * OS의 성능에 큰 영향을 줌
* 불필요한 Context Switching을 줄이는 것이 중요 
    * 예, 스레드(thread) 사용 등 
