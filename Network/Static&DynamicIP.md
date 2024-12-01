# 정적 IP 주소와 동적 IP 주소

### 정적 할당

- 호스트에 직접 (수작업) IP주소를 부여하는 방식
- 이렇게 할당된 주소 주소 = 정적 IP주소 (static IP address)
- 윈도우나 맥OS 등의 네트워크 설정에서 다음 화면 처럼 IP 주소를 수동으로 설정
- 일반적으로 부여하고자 하는 IP주소, 서브넷 마스크, 게이트웨이(라우터) 주소, DNS 주소를 입력

### 기본 게이트웨이

- 게이트웨이의 일반적인 의미
    - 서로 다른 네트워크를 연결하는 하드웨어적/소프트웨어적 수단
    - 기본 게이트웨이
        - 호스트가 속한 네트워크 외부로 나가기 위한 기본적인 첫 경로 (첫 번째 홉)
        - 네트워크 외부와 연결된 라우터의 주소를 의미하는 경우가 많음
        - IP 할당의 맥락에서 사용된 ‘게이트웨이’라는 용어는 기본 게이트웨이(라우터<공유기>의 주소)를 의미

### 모든 IP 주소를 정적으로 할당할 수 있을까

- 호스트 수가 많아질 경우 관리 곤란
- 의도치 않게 잘못된 IP 주소를 입력할 수도 있고, 중복된 IP 주소를 입력할 수도 있음

### 동적 할당

- 호스트에 IP 주소를 프로토콜을 활용해 자동으로 할당하는 방식
    - IP 동적 할당에 사용되는 대표적인 프로토콜 DHCP(Dynamic Host Configuration Protocol)
- 이렇게 할당된 IP 주소를 동적 IP 주소(dynamic IP address)라고 함
- DHCP를 통한 IP 주소 할당
    - 클라이언트와 DHCP 서버 간 메시지 송수신을 통해 할당이 이루어짐
    - 클라이언트: IP 주소를 할당받고자 하는 호스트
    - DHCP 서버: 호스트에게 IP 주소를 제공하는 호스트
        - DCP 서버의 역할은 일반적으로 라우터(공유기)가 수행
        - 특정 호스트에 DHCP 서버 기능을 추가할 수도 있음
        - DHCP 서버는 클라이언트에게 할당 가능한 IP 주소 목록을 관리하다, 클라이언트 요청시 IP 주소를 할당
        - DHCP로 할당받은 동적 IP 주소는 사용할 기간(임대 기간) 이 정해짐
            - 일반적으로 수 시간에서 수 일
            - 임대 기간이 끝난 IP 주소는 다시 DHCP 서버로 반납
              
        <img width="434" alt="스크린샷 2024-11-04 오전 8 42 00" src="https://github.com/user-attachments/assets/92da5a7b-0458-482e-ac0f-da3ea6d60fb3">
        - IP 주소 할당 과정에서 주고 받는 메세지
            - DHCP Discover
                - DHCP 서버를 찾는 메시지
                - 브로드캐스트로 전송
                - 클라이언트는 아직 IP 주소를 할당받지 못함: 송신지 IP 주소는 0.0.0.0으로 설정
            - DHCP Offer
                - 클라이언트에게 할당 가능한 IP 주소 정보를 제안하는 메시지
                - 할당가능한 IP 주소, 서브넷 마스크, 임대 기간 등의 정보 포함
            - DHCP Request(클라이언트 → HDCP 서버)
                - DHCP Offer 메시지에 대한 응답
                - 브로드캐스트로 전송
            - DHCP Acknowledgment(DHCP ACK)
                - 최종 승인과 같은 메시지
                - DHCP ACK 메시지를 클라이언트는 이제 할당 받은 IP 주소를 자신의 IP 주소로 설정 후 
                임대 기간 동안 IP 주소 사용
                - 사용 기간이 모두 끝나면?
                    - IP 주소를 DHCP 서버에 반납
                    - 원칙적으로는 다시 DHCP Discover - DHCP Offer - DHCP Request - DHCP ACK 주고 받아 IP 주소 재할당
                - 임대 갱신(lease renewal)
                    - IP 주소 임대 기간이 끝나전에 임대 기간을 연장하는 것
                    - 임대 기간이 끝나기 전에 기본적으로 두 차례 자동으로 수행
                    - 자동 임대 갱신이 모두 실패하면 그 때 IP 주소 반납