# TCP 3-way-handshake

## TCP 3-way-handshake에 앞서서

### 1. TCP 3 - way-handshake란?

- TCP / IP 프로토콜을 이용해서 통신을 하는 응용 프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해서 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미한다.

### 2. TCP?

- TCP 프로토콜은 기존의 데이터 손실을 일으키는 데이터 전송 통신 프로토콜과 달리
- 전송 단위는 세그먼트
- 흐름 제어, 오류 제어, 순서 제어 등을 이용해서 신뢰적인 연결 지향성 서비스를 제공합니다.
- UDP와는 다르게 양 프로세스 간의 연결이 HandShaking이 선행된 후 데이터를 전송합니다.
- 양방향 통신입니다.
- 전송 계층에 속하는 프로토콜이다.

### 3. 전송 계층?

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6c8795cc-5f84-4008-9d66-7b4d66fe827c/c2ab752d-d4f4-44b7-a220-3c4c6df3f950/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6c8795cc-5f84-4008-9d66-7b4d66fe827c/22fc1bb1-bfd3-4f0f-8ef9-5760ea50d7d4/Untitled.png)

- 전송 계층은 네트워크 구성요소와 프로토콜 내에서 송신자와 수신자를 연결하는 통신 서비스를 제공한다고 한다.
- 양쪽의 end to end 간의 데이터 전송을 담당하는 역할을 하는 계층이다.

### 4. 전송계층과 데이터 링크 계층의 차이

- 데이터 링크 계층은 물리적인 연결을 한다.
  - 서버가 물리적으로 연결되어 있다는 것은 컴퓨터와 컴퓨터를 직접적으로 선으로 연결한 경우를 의미한다.
- 전송 계층은 논리적인 연결을 담당한다.
  - 서버가 논리적으로 연결되어 있다는 것은 서버와 클라이언트 사이에 무수히 많은 노드를 거쳐 연결된다는 의미다.
  - 이때 전송 계층의 SYN, ACK를 통한 서로의 존재를 확인함에도 불구하고 중간 노드의 결함등이 발생하면 이 연결은 유효하지 않다고 판단합니다.
  - 이러한 이유 때문에 논리적으로 연결된 것이라고 가정(가상연결)이라고 볼 수 있습니다.

### 5. TCP/IP 프로토콜을 이용해 통신을 하는 응용 프로그램의 종류

- SMTP(e-mail)
- FTP(file transfer protocol) : 전송기기 간에 데이터 교환을 위한 통신 규약, 파일을 전송할 때 사용
- 웹 HTTP

## 다시 돌아와 본론으로

### 1. TCP 3-Way-Handshake?

- 간단하게 전송 제어 프로토콜(TCP)에서 통신하는 장치 간에 서로 잘 연결되어 있는지 확인하는 과정/방식이라고 생각하면 된다.
- 송수신자(데이터를 주고 받는 주체들을 생각) 사이에서 연결을 확인해주는 것을 생각하면 된다.

### 2. 3-Way-Handshake 구조

2-1. status

- Closed : 닫힌 상태
- LISTEN : 포트가 열린 상태로 연결 요청 대기 중
- SYN_RCV : SYNC 요청을 받고 상대방의 응답을 기다리는 중
- ESTABLISHED : 포트 연결 상태

2-2. 구조

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/6c8795cc-5f84-4008-9d66-7b4d66fe827c/a5194536-ed3a-4af0-bbb8-81c33ea6dbf3/Untitled.png)

1. client의 포트는 closed 상태이고 server측의 포트는 listen 상태이다. 이때 클라이언트에서 서버에 연결을 위해 SYN 데이터를 보낸다.
   - 클라이언트 측에서 서버 측으로 요청 전달
2. 이때 서버의 포트는 listen에서 SYN_RCV 상태로 변경 된다. 그리고 요청을 정상적으로 받았다는 대답 = ACK과 클라이언트도 포트를 열어달라고 하는 SYN를 같이 보내준다.
   - 요청에 따른 응답과 새로운 요청을 클라이언트 측으로 전달
3. 클라이언트에선 ACK+SYN 응답을 받고 ESTABLISHED로 포트 상태 변경을하고 이를 잘 변경했다는 응답을 다시 서버측으로 보내준다.
   - 응답을 확인하고 해당 요청에 따른 변경과 이에 대한 응답 전달
4. 서로 ESTABLISHED로 변경되면서 연결이 되게 된다.

## 정리

- TCP는 전송 계층에서 사용하는 프로토콜로 안전성이 보장된 프로토콜이다.
- TCP를 이용해서 데이터를 전송하기 전에 3-way-handshake라는 작업을 먼저 진행해 연결하고자 하는 장치 간에 잘 연결이 되었는지 확인을 하고 데이터 전송을 한다.
- TCP는 전송 데이터를 세그먼트로 분할하고 TCP 헤더와 함께 전송한다.
