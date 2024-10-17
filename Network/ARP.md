# ARP (Address Resolution Protocol)

- IP 주소를 통해 MAC 주소를 알아내는 프로토콜
    - 동일 네트워크 내에 있는 송수신 대상의 IP 주소를 통해 MAC 주소를 알아낼 수 있음
- ARP 동작
    - ARP 요청
    - ARP 응답
    - ARP 테이블 갱신
- e.g.
    - 동일 네트워크에 속한 호스트 A,B
    - 호스트 A는 호스트 B의 IP 주소는 알지만 MAC 주소는 모름
    - 이 상황에서 호스트 B의 MAC 주소를 알아내는 과정

### ARP 요청 (ARP Request)

- 호스트 A:  브로드캐스트 메시지 전송
- 이 브로드캐스트 메시지 = ARP 요청이라는 ARP 패킷

### ARP 응답 (ARP Reply)

- 호스트 B외에 나머지 호스트는 자신의 IP주소가 아니므로 무시
- 호스트 B: 자신의 MAC 주소를 담은 유니캐스트 메시지를 A에게 전송
- 이 유니캐스트 메시지 = ARP 응답이라는 ARP 패킷
    - 이 메시지를 수신한 A는 B의 MAC주소를 알게 됨

### ARP 패킷?

- ARP 요청, ARP 으답 과정에서는 송수신되는 패킷
    - 오퍼레이션 코드(Opcode; Operation Code) - ARP 요청의 경우 1, ARP응답의 경우 2
    - 송신지 하드웨어 주소(Sender Hardware Address) 수신지 하드웨어 주소(Target Hardware Address)
    - 송신지 프로토콜 주소(Sender Protocol Address)와 수신지 프로토콜 주소(Target Protocol Address)
<img width="781" alt="스크린샷 2024-10-17 오전 8 59 50" src="https://github.com/user-attachments/assets/65275843-6d4f-48d7-a580-45fd13f5a640">

### ARP 테이블 갱신

- ARP 테이블(ARP Table): ARP 요청-응답을 통해 알게 된 IP 주소와 MAC 주소의 연과 관계
    - ARP 테이블 항목은 일정 시간이 지나면 삭제, 임의 삭제도 가능
    - ARP 테이블에 등록된 호스트에 대해선 ARP 요청을 보낼 필요 없음

### ARP 테이블 확인

- 윈도우 명령 프롬프트 (CMD)나 맥OS 터미널에서 arp -a를 입력
<img width="413" alt="스크린샷 2024-10-17 오전 9 02 54" src="https://github.com/user-attachments/assets/c8a42ee0-a30d-40ea-a186-5bde79d092db">

### 통신하고자 하는 호스트 A와 B가 서로 다른 네트워크에 속해 있을 경우

- ARP 요청 - ARP 응답 과정을 통해 라우터 B의 MAC 주소를 알아낸 뒤, 이를 향해 패킷 전송
    - 네트워크 별로 ARP가 실행된다
