# 스위치

- 허브의 충돌 문제
    - CSMA/CD로 어느 정도 완화할 수 있었지만 보다 근본적인 해결 방법 존재
    - 전달 받은 신호를 수신지 호스트가 연결된 포트로만 내보내고, 전이중 모드로 통신하면 된다.
- 이를 위한 장비가 바로 스위치(Switch)
- 허브와는 달리 특정 MAC 주소를 가진 호스트에만 프레임 전달 가능
- 전 이중 모드 통신 지원
    - CSMA/CD 프로토콜이 필요하지 않음

### 스위치의 주요 기능

- 스위치의 MAC 주소 학습 기능
    - 전달 받은 신호를 원하는 포트로만 내보냄
    - 포트별로 콜리전 도메인이 나누어지기에 충돌 위험이 감소
- 스위치의 VLAN 기능
    - 논리적으로 LAN을 분리하는 가상의 LAN, VLAN 구성 가능

### 스위치의 MAC 주소 학습 기능 (MAC address Learning)

- 특정 포트와 해당 포트에 연결된 호스트의 MAC 주소와의 관계를 기억
- 원하는 호스트에만 프레임 전달
- MAC. 주소 테이블(MAC address table)
    - 스위치 포트와 연결된 호스트의 MAC 주소 간의 연관 관계를 나타내는 정보
        - 플러딩
        - 포워딩과 필터링
        - 에이징
        

e.g. → 호스트 A가 C로 메세지를 전하는 과정

- 학습 전에는 MAC주소 테이블이 지워져있다
- MAC 주소 학습: 프레임 내 송신지 MAC주소 필드를 바탕으로 이루어짐
- 수신지 맥주소를 모르기 때문에 허브처럼 모든 수신지에 프레임 전송
    - 상기의 행동을 플러딩이라고 부른다
- 호스트 C는 응답 프레임을 스위치로 전송
- 송신지 MAC 주소 필드로 호스트 C의 MAC 주소 학습
- 호스트 AC는 한 번 플러딩을 해서 MAC 주소 테이블에 기록되었기 때문에 플러딩이 필요 없다.
- 호스트 A가 C에게 프레임을 전송하면
- 스위치는 호스트 B,D가 연결된 포트로는 내보내지 않도록 필터링(filtering)
- 호스트 C가 연결된 포트로 프레임을 포워딩(forwarding)
- 에이징
    - 만약 MAC주소 테이블에 등록된 포트에서 일정 시간 동안 프레임을 받지 못하면 해당 항목은 삭제
    - 일정 시간 동안 ‘송신지 MAC 주소’가 ac:cd:ad:cd:00:01인 프레임을 1번 포트에서 못 받으면 이 항목은 삭제

### 스위치의 VLAN 기능

- VLAN(Virtual LAN) - 한 대의 스위치로 가상의 LAN을 만드는 방법
    - 불필요한 트래픽(허브 스위치의 플러딩)으로 인한 성능 저하 방지
    - “한대의 물리적 스위치라 해도”, “마치 여러 대의 스위치가 있는 듯이”, “호스트의 물리적 위치와 관계 없이”
    - VLAN은 사실상 다른 LAN : 서로 다른 네트워크로 간주, 브로드캐스트 도메인 달라짐
        - 따라서 LAN끼리 통신하려면 3계층 이상의 장비가 필요하다

### VLAN의 종류: 포트 기반 VLAN (port based VLAN)

- 스위치의 포트가 VLAN을 결정하는 방식
- 특정 포트에 VLAN을 할당한 뒤, 해당 포트에 호스트를 연결하여 VLAN에 참여
    - 호스트 A와 B는 VLAN2를 할당한 포트에 연결되어 있으므로 같은 LAN에 속한 셈
    - 호스트 C는 VLAN3에 속해 있으므로 호스트 A,B와는 다른 LAN에 속한셈
    - 정적 VLAN

### MAC 기반 VLAN (MAC based VLAN)

- 사전에 설정된 MAC 주소에 따라 VLAN이 결정
- 송수신하는 프레임 속 MAC 주소가 호스트가 속할 VLAN을 결정하는 방식

### 참고) 브리지

- 브리지(Bridge)는 데이터 링크 계층의 스위치와 유사한 장비
    - 네트워크 영역을 구획하여 콜리전 도메인을 나누거나 네트워크를 확장
    - 브리지는 앞서 설명한 스위치의 기능들도 제공
        - MAC 주소를 학습, 포워딩, 필터링
    - 다만 최근에는 스위치에 비해 사용 빈도가 줄어드는 추세
    - 일반적으로 스위치의 성능이 우세하기 때문
    - 개념적으로는 계속 쓰인다
