
### 컴퓨터 구조 
	⁃	컴퓨터의 구조는 4가지의 컴포넌트로 나눌 수 있다. 
	⁃	하드웨어: 기초적인 컴퓨팅 자원을 제공한다( CPU, Memory, I/O devices)
	⁃	OS: 다양한 어플리케이션과 유저 사이에서 하드웨어를 제어하고 협응한다. 
	⁃	어플리케이션 프로그램: 유저들의 컴퓨팅 문제를 해결해줄 시스템
	⁃	ex) 워드 프로세서, 컴파일러, 웹브라우저, 데이터베이스, 비디오 게임 
	⁃	사용자: 사람, 머신, 다른 컴퓨터들 
	⁃	하드웨어가 가장 밑단 계에 있고, 그 위에 OS가 있다( OS도 프로그램이지만 가장 밑에 들어간다.)
	⁃	그 위에 시스템과 어플리케이션이 들어간다. 

### Operating System 정의 
	⁃	User View vs. System View 
	⁃	User View
	⁃	사용이 쉽고
	⁃	프로그램을 실행해준다.
	⁃	OS View 
	⁃	OS는 자원할당을 한다. 
	⁃	모든 자원을 관리한다 ( 하드웨어 포함 )
	⁃	동일한 자원에 동시에 접근했을 떄 제어한다. 
	⁃	OS는 제어 프로그램이다. 
	⁃	프로그램의 실행을 제어한다. 
	⁃	에러와 적절하지 않은 자원의 사용을 막기 위해 ( 프로그램이 깨지지 않게 보호 )

### Operating System Definition (Cont.)
	⁃	모두 통용되는 정의는 아니다. 
	⁃	‘당신이 OS 시스템을 주문하면 모든 벤더들이 담아주는 모든 것’ 이지만 엄청 다양하다. 
	⁃	‘프로그램에 항상 상주하는 프로그램’ 은 Kernel이다. 
	⁃	Kernel을 OS의 한 부분이다( 그러나 매우 큰 부분이다)
	⁃	항상 메모리에 상주한다.
	⁃	OS라 함은 주로 커널이라 생각할 때가 많다. 

### Computer Startup 
	⁃	BootStrap Program OS를 끌어당겨서 컴퓨터를 시작하게 해준다.
	⁃	일반적으로 ROM( Read Only Memory )나 EEPROM에 저장되어있는 펌웨어이다. 
	⁃	각종 초기화나 진단을 해준다. 
	⁃	마지막 단계로 커널을 불러오고(Disc에서 가져온다) 실행한다. 
	⁃	OS가 올라가야지 Disc Access가 가능하다.
	⁃	Bootstrap에서부터 시스템을 초기화 하고 시작한다. 

### Computer System Organization 
	⁃	Computer-System Operation 
	⁃	한 개나 한 개 이상의 CPU, Device Controller가 공유 메모리에 접근을 제공하는 버스에 연결되어있다. 
	⁃	하나의 메모리를 공유하기 때문에 경쟁을 한다. 

### Computer System Operation 
	⁃	I/O Devices 와 CPU가 병렬적으로 실행된다. 
	⁃	각각의 Device Controller는 특정 장치에 대한 책임을 갖는다. 
	⁃	각각의 Device Controller는 자체 버퍼를 가지고 있따. 
	⁃	CPU는 데이터를 메인 메모리에게 주고 컨트롤러에 버퍼를 통해 정보를 가져온다. 
	⁃	I/O는 장치로 부터 버퍼 컨트롤러로 데이터를 옮긴다. 
	⁃	Device Controller는 CPU에게 interrupt를 통해 알려준다. 

### Common Function of Interrupts 
	⁃	Interrupt가 들어오면 서비스 제어권이 넘어간다. 
	⁃	현재 실행하던 프로그램의 주소를 Intupprt 구조에서 반드시 저장한다. 
	⁃	새로 들어온 Interrupt는 다른 Interrupt가 끝나기 전까지 들어오는 것이 불가능하다. Interrupt 유실을 막기 위해서이다. 
	⁃	Trap은 Software-Generated와 에러나 유저의 요청에 의해서 생긴다. 
	⁃	Operating System은 Interrupt Driven이다.
	⁃	H/W Interrupt 
	⁃	S/W Interrupt: trap 

### Interrupt TimeLine 
	⁃	Interrupt tarnsfer Done ( 전송이 끝나면 )
	⁃	유저 프로그램을 중단하고 
	⁃	I/O 처리를 한다. 
	⁃	다시 유저 프로그램을 실행한다. 

### Two I/O Methods 
	⁃	동기방식 Process가 끝날 때 까지 기다린다. 
	⁃	비동기 방식 바로 일을 시작하고 끝났다고 알려줌 

### Operating Ststem Structure 
	⁃	Multiprogramming은 효율성을 위해 필요하다 
	⁃	단일 유저는 CPU와 I/O Device를 항상 바쁘게 유지할 수 없다. 
	⁃	멀티프로그래밍은 코드와 데이터로 조직된 일이기 때문에 CPU는 항상 실행할 일을 가지고 있다. 
	⁃	모든 작업의 부분집합은 메모리에 지속적으로 있다. 
	⁃	하나의 작업은 Job Scheduling을 통해 선택 되고 실행된다. 
	⁃	CPU가 대기해야할 때 (ex: I/O 때문에 ) 다른 작업으로 바꿔줌 
	⁃	Time Sharing ( MultiTasking ) 
	⁃	짧게 CPU를 할당하여 여러가지 프로그램을 사용할 수 있게 한다. 
	⁃	CPU의 작업을 빈번하게 바꾸면서 각각의 작업이 실행되면서 유저와 상호작용할 수 있다. 
	⁃	Response Time 은 Should be < 1 second 
	⁃	각각의 유저는 최소 실행되는 프로그램이 메모리에 있어야 한다. ( Process )
	⁃	만약 다수의 동시에 실행되려고 대기중이라면 ( CPU Scheduling )
	⁃	만약 프로세스가 메모리에 맞지 않는다면, 스와핑을 통해 실행되도록 해준다. 

	⁃	Time Sharing과 Multi Programming의 가장 큰 차이는 
	⁃	Time Sharing ( CPU Schediling ) 
	⁃	Multi Programming ( Job Scheduling ) 

### Operating System Operations 
	⁃	하드웨어를 통한 interrupt 
	⁃	소프트웨어 또는 요청이 만든 Exceiption 이나 Trap 
	⁃	( Division by Zero, Request for operating system sercie) 
	⁃	프로세스 문제는 무한 루프나, 프로세스가 서로를 변경하려고 하거나 OS를 변경하려고 하는 것들을 포함한다.
	⁃	Dual Mode는 OS가 스스로의 시스템과 컴포넌트를 지키도록 해준다. 
	⁃	User Mode 와 Kernel mode가 있다. 
	⁃	Mode bit는 하드웨어에 의해 제공 된다.
	⁃	시스템이 실행될 때 유저코드 또는 커널 코드를 구분할 수 있는 능력을 제공 
	⁃	어떤 수행은 오직 커널에서만 실행되도록 특권 처럼 디자인 된다. 
	⁃	시스템 콜은 유저 모드를 커널 모드로 바꿔주고, 다시 유저에게 반환한다. 

### Transition from User to Kernel Mode 
	⁃	유저 프로세스가 실행되고 있다.  ( mode bit = 1 ) 
	⁃	유저 프로세스단에서 시스템 콜릉ㄹ 부른다. ( 커널에 서비스를 요청 )
	⁃	Trap 발생 ( mode bit = 0 ) 
	⁃	Excute System Call ( 하드웨어에 접근할 특권을 얻게 됨 ) 
	⁃	return ( mode bit = 1 ) 
	⁃	유저 프로세스 단으로 다시 돌아온다 ( return from system call ) 

### Process Management 
	⁃	Process란 실행중인 프로그램이다. 
	⁃	프로세스는 시스템의 일의 단위이다. 
	⁃	프로그램은 수동적인 엔티티이고, 프로세스는 동적인 엔티티이다. 
	⁃	프로세스는 자원을 할당 받아야 한다. 
	⁃	CPU, Memory, I/O, files, Initialization data 
	⁃	프로세스의 종료는 모든 재사용 가능한 자원을 반납해야한다. 
	⁃	단일 스레드 프로세스는 하나의 프로그램 카운터를 가지고있고 다음에 실횡될 곳의 주소를 가지고있다.
	⁃	프로세스는 순차적으로 한 개씩 완료될 때 까지 실행된다.
	⁃	멀티 스레드 프로세스는 스레드마다 프로그램 카운터를 가지고있다. 
	⁃	일반적으로 시스템은 많은 프로세스를 가지고 있고, 어떤 유저와 어떤 OS에서 단일 혹은 여러 개의 CPU에서 Concurrent하게 실행된다. 
	⁃	CPU와 프로세스와 / 스레드간의 다중화로 인한 동시성 

### Process ManageMent Activites 
	⁃	OS는 프로세스 관리에 대해서 다음과 같은 활동과 연관이 있다. 
	⁃	유저와 시스템 프로세스에 대한 생성과 삭제 
	⁃	프로세스의 Suspending과 재개 
	⁃	프로세스 동기화에 대한 메커니즘 제공 
	⁃	프로세스 소통에 관한 메커니즘 제공 
	⁃	데드락(교착 상태 - 자원을 서로 잡고 안 놔주는 경우)에 대한 처리 메커니즘 제공

### Memory Management 
	⁃	프로세싱 전후에 모든 데이터는 메모리에 올라온다. 
	⁃	모든 수행은 실행되기 위해 메모리에 올라온다. 
	⁃	메모리 관리는 CPU 활용률과 와 컴퓨터가 유저에게 반응하기 위한 최적화하기 위해 메모리에 뭘 올릴지 결정한다
	⁃	Memory Management Activities 
	⁃	계속 추적한다 어떤 파트의 메모리가 현재 상되고 누구에 의해 사용되는지 
	⁃	어떤 프로세스나 데이터가 메모리에 들어오고 나갈지 결정한다. 
	⁃	필요에 따라 메모리 공간을 할당하고 회수한다. 

### Storage Management 
	⁃	OS는 규격과 저장 정보의 논리적인 뷰를 제공한다. 
	⁃	물리적인 프로퍼티들을 논리적 저장 단위로 추상화한다. ( file ) 
	⁃	FileSystem Management 
	⁃	파일이 모여서 디렉토리가 됨 
	⁃	대부분의 프로그램에서 접근 제어는 누가 접근할 수 있는지 결정하는 것이다. 
	⁃	OS Activities Include
	⁃	파일과 디렉토리를 생성한다.
	⁃	원시적으로 파일과 디렉토리를 조작한다. 
	⁃	파일을 제 2 저장소에 맵핑한다. 
	⁃	파일을 안정된 저장소에 백업한다. 

### Mass Storage management 
	⁃	일반적으로 디스크는 메인메모리에서 사용되는 게 맞지 않는 데이터를 저장하거나 긴 기간 저장해야 하는 데이터를 저장할 때 쓰인다. 
	⁃	적절한 관리가 가장 중요하다. 
  ⁃ 컴퓨터 작동의 전체 속도는 디스크 서브 시스템과 그 알고리즘에 달려있다 
	⁃	OS Activities 
	⁃	Free Space Mangement 
	⁃	저장 공간 할당 
	⁃	디스크 스케줄링 

### I/O Subsystem 
	⁃	OS의 목표중 하나는 특정 하드웨어 장치의 특성을 숨겨준다
	⁃	유저들이 디바이스의 특성을 하나하나 다 알고 사용하고 대응하려면 피로도가 엄청 상승한다. 
	⁃	I/O subsystem responsible for 
	⁃	I/O 버퍼링(전송되는 동안 잠시 데이터를 보관한다), 캐싱( 빠른 저장소에 일부 데이터를 퍼포먼스를 위해 저장해놓는다),  Spooling 의 데이터 관리를 한다. 
	⁃	디바이스 드라이버 인터페이스 
	⁃	하드웨어 장치에 대한 드라이버 

### Protection and Security 
	⁃	Protection: Access나 Process에 의한 자원 보호 
	⁃	Security
	⁃	내부 외부에 대항한 방어 시스템
	⁃	시스템이 유저들간에서 누가 어떤 것을 해도 되는지 구별한다. ( Access Controll ) 
	⁃	User 식별된다 (user ID, security IDs) 각 유저에 대해서 이름과 연관되어 있는 번호로
	⁃	User ID 와 연관된 모든 파일과 프로세스의 엑세스 컨트로를 결정한다. 
	⁃	Group Identifier는 허락한다 사용자 집단에게 정의 되고 제어 관리되도록, 또한 각각의 파일과 프로세스에 연관 되도록
	⁃	Privileage esclation 특정 아이디가 더 큰 권한을 갖도록 허락해준다. ( Root 권한을 갖게할 것인지 아닌지 ) 
