### 연결지향형 서비스

애플리케이션 계층 메시지를 전송하기 전에 클라이언트와 서버가 서로 전송 제어 정보를 교환하게 한다.
이를 **핸드셰이킹**이라고 하며 이 단계를 지나면 TCP 연결이 두 프로세스의 소켓 사이에 존재하게 된다.

이 연결로 서로에게 동시에 메시지를 보낼 수 있기 때문에 **전이중(full-duplex) 연결**이라고 한다.
### 신뢰적인 데이터 전송 서비스

TCP는 애플리케이션에서 바이트 스트림을 소켓으로 전달하면 손실되거나 중복되지 않게 수신 소켓으로 전달한다.

### 혼잡 제어 방식

통신하는 프로세스의 직접 이득보다는 인터넷의 전체 성능 향상을 위한 서비스를 포함
특히, TCP 혼잡 제어는 각 TCP 연결이 네트워크 대역폭을 공평하게 공유할 수 있게끔 제한