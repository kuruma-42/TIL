        - 

1. 시스템 콜
- 정의: 시스템 호출(system call)은 운영 체제의 커널이 제공하는 서비스에 대해, 응용 프로그램의 요청에 따라 커널에 접근하기 위한 인터페이스이다.
- mode bit 를 가지고 설명
    * 유저 프로세스가 실행되고 있다. ( mode bit = 1 )
    * 유저 프로세스단에서 시스템 콜한다 부른다. ( 커널에 서비스를 요청 )
    * Trap 발생 ( mode bit = 0 )
    * Excute System Call ( 하드웨어에 접근할 특권을 얻게 됨 )
    * return ( mode bit = 1 )
    * 유저 프로세스 단으로 다시 돌아온다 ( return from system call )


2. Context Switching
    - 개념, 내용, 언제 사용되는지, 어떤식으로 구현되는지
- 개념
    - 멀티프로세싱을 지원하는 OS에서 실행 중인 프로세스를 멈추고 다른 프로세스를  실행하고자 결정하면 커널에서 현재 실행 중이던 프로세스의 정보를 나중에 다시  실행될 때를 대비하여 현재 상태를 PCB를 저장하고 새롭게 실행되는 프로세스의 정보를 CPU가 사용할 수 있도록 load한 후 프로세스 코드를 실행시키는데 이러한 과정을 Context Switching이라 한다. 
- 구동 방식 
    - Process는 다양한 원인에 의해 중간에 종료될 수 있다.  (interrupt나 system call에 의해서)  종료되는 P0의 상태를 PCB0(Process Control Block) 저장한다.  새로 시작될 P1의 상태를 PCB1에서 불러오고 해당 프로세스를 실행한다.  상기와 같은 방식으로 Context Switching이 일어난다. 
￼![admitted](https://github.com/kuruma-42/TIL/assets/60722292/89f8315e-5047-4741-a8ef-eaadf7c50634)

 

3. Thread
- 스레드의 개념: 기본적인 CPU활용의 단위이다. ( 프로세스의 경량화된 방식 ) 
    - 한 프로세스 내의 실행의 흐름 
- 장점
    - 많은 자원을 공유하기 때문에 반응이 빠르고
    - 자원공유로 자원을 효율적으로 쓸 수 있고
    - 경제적이고
    - Multi Process 방식에 적합하다 

4.Process 
- 프로세스의 개념: 실행중인 프로그램
- 프로세스의 상태: new, running, waiting, ready, terminated 
- 프로세스의 동작
    - new: job queue에 올라가고 어떤 것을 메모리에 올릴지 job scheduler가 정한다. 
    - ready: ready queue에서 CPU할당을 대기한다 (CPU scheduler가 정한다.)
    - running: CPU를 할당 받은 상태
    - wating: I/O 나 이벤트가 있을 때 대기 상태가 된다. 이벤트가 끝나면 다시 ready queue로 간다. 
    - terminated: 실행이 끝난 상태  

- Process 와 Thread의 차이 
    - Process간 자원 공유가 안 되지만 Thread는 공유가 된다 
    - 스레드는 프로세스 내에서 동작하기 때문에 메모리 영역을 독립적으로 받지 못함  
- 프로세스 대신 쓰레드를 사용 시 장점이 무엇인지 논하라
    * Code, Data, Heap의 영역을 공유하기 때문에 Context Switching이 빠름
    * 새로운 프로세스를 생성하는 것이 아니므로 생성과 소멸도 빠르다.
    * 쓰레드간 통신 방법이 훨씬 간단함.
