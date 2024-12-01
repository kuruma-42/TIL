# UDP feat.Python


### UDP server 
```python
from socket import *

# 서버 포트 세팅
server_port = 12000
# 비연결성(SOCK_DGRAM 유형)
# 비연결성 AF_INET 소켓은 전송 프로토콜로 사용자 데이터그램 프로토콜(UDP)를 사용
server_socket = socket(AF_INET, SOCK_DGRAM)
# 포트와 소켓 바인딩
server_socket.bind(('', server_port))
print("The server is ready to receive")
while True:
    # 클라이언트로 부터 데이터 수신 (recvfrom)
    message, address = server_socket.recvfrom(2048)
    print('Client IP Address :', address[0])
    # meassage를 UpperCase로 바꿔준다.
    modifiedMessage = message.decode().upper()
    # 서버 소켓을 통해 UpperCase로 바꾼 메세지를 인코딩해 클라이언트로 송신한다.
    server_socket.sendto(modifiedMessage.encode(), address)

```

### UDP client
```python
from socket import *

# 서버 로컬로 세팅
server_name = '127.0.0.1'
# 서버 포트 세팅
server_port = 12000
# 비연결성(SOCK_DGRAM 유형)
# 비연결성 AF_INET 소켓은 전송 프로토콜로 사용자 데이터그램 프로토콜(UDP)를 사용
client_socket = socket(AF_INET, SOCK_DGRAM)
# 메세지 입력
message = input('Input lowercase sentence: ')
# lowerCase 메세지를 인코딩한 파라미터와
# 서버 이름과 서버 포트 넘버를 파라미터를 넣어준다.
client_socket.sendto(message.encode(),(server_name, server_port))
# 클라이언트 소켓은 2048
modifiedMessage, address = client_socket.recvfrom(2048)
print("From Server:", modifiedMessage.decode())
# 소켓 종료
client_socket.close()

```
