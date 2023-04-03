# 💻 HTTP/1.1 vs HTTP/2.0 vs HTTP/3.0

## 👨🏻‍💻 HTTP/1.1과 HTTP/2.0 차이점

### 1. 프로토콜 형태

<img width="500" alt="스크린샷 2023-03-20 오후 2 24 24" src="https://user-images.githubusercontent.com/64779472/226253737-1a88c165-72df-4c41-a493-c16bbcd100c7.png">

- HTTP 1.1은 `텍스트 기반의 프로토콜`입니다. 따라서 전송 데이터의 용량이 크다.
- 반면에, HTTP 2.0은 `이진 형태의 프로토콜`로, 전송 데이터의 용량이 작아져서 데이터 전송을 더 효율적으로 처리할 수 있다.

<br />

### 2. 다중화(Multiplexing)

<img width="457" alt="스크린샷 2023-03-20 오후 2 08 03" src="https://user-images.githubusercontent.com/64779472/226251732-f09971cf-402c-449e-affd-46648cf735c1.png">

- HTTP 1.1은 기본적으로 `하나의 TCP 연결을 통해 하나의 요청과 응답을 처리한다.`
  - 따라서, 여러 개의 요청을 처리하기 위해서는 여러 개의 TCP 연결이 필요했다. 이는 불필요한 지연과 복잡성이 발생했다.
- 하지만 HTTP 2.0은 하나의 TCP 연결에서 여러 개의 요청과 응답을 동시에 처리할 수 있도록 `다중화(Multiplexing)`를 지원한다.
  - 이를 통해, 여러 개의 요청과 응답을 `병렬`로 처리하면서, 불필요한 대기 시간을 줄이고, 전송 속도를 높일 수 있다.

```
참고로 HTTP/1.1에서 Keep-Alive를 사용하면 요청을 보내고 반환을 받은 후에도 커넥션을 유지할 수 있다.
하지만 위의 이미지에서 중간 Piplined HTTP처럼 [요청-응답][요청-응답]형태로 반복된다.
이미지의 오른쪽 Multiplexed HTTP처럼 병렬적으로 처리하는 것은 불가능하다.
```

<br />

### 3. 헤더 압축

<img width="500" alt="스크린샷 2023-03-20 오후 2 24 45" src="https://user-images.githubusercontent.com/64779472/226253787-fa03824c-02c1-413c-97d2-b22cf59c140e.png">

- HTTP 1.1은 헤더 정보가 텍스트 형태로 전송되기 때문에, 헤더 크기가 커지면 불필요한 대기 시간이 발생할 수 있다.
  - 예를들어, 클라이언트가 두 번의 요청을 보낸다고 가정하면, HTTP 1.1은 두 개의 요청 Header를 중복값이 존재해도 그냥 중복 전송을 진행한다.
- 반면에 HTTP 2.0은 헤더 정보를 압축해서 전송하기 때문에, 불필요한 대기 시간을 최소화하면서, 전송 속도를 높일 수 있습니다.
  - 이때, HTTP 2.0은 Header 정보를 `HPACK 압축방식`을 이용하여 압축 후 전송한다. HPACK은 `Huffman 코딩`과 `정적/동적 테이블`을 이용하여 중복되는 헤더 정보를 압축합니다.
  - HTTP 2.0에서는 중복되는 헤더 정보를 `정적/동적 테이블`에 저장하고, `인덱스 번호`로 참조함으로써 중복 전송을 피한다.

<br />

### 4. 서버 푸시(Server Push)

<img width="714" alt="스크린샷 2023-03-20 오후 2 22 31" src="https://user-images.githubusercontent.com/64779472/226253533-65baec3b-3665-417c-8767-f72c4a27ad6e.png">

- HTTP 2.0은 `서버 푸시(Server Push)`라는 기능을 지원한다. 이 기능을 사용하면, 서버에서 클라이언트의 요청에 대한 응답으로 데이터를 보내는 것뿐만 아니라, 클라이언트가 요청하지 않은 데이터도 미리 보낼 수 있다.
  - HTTP1.1에서는 웹 페이지에서 HTML 파일을 요청하면 서버는 해당 HTML 파일을 전송한다. 이때 HTML 파일에서 사용하는 `이미지`, `스크립트`, `스타일시트` 등의 리소스는 클라이언트가 요청해야만 전송된다.
  - 하지만, 서버 푸시를 사용하면 서버가 HTML 파일을 전송하는 동시에 해당 `HTML 파일에서 사용하는 리소스를 미리 클라이언트에게 전송`할 수 있습니다.
- 이를 통해 클라이언트는 추가적인 요청 없이 더 빠르게 페이지를 로딩할 수 있으며, 서버와의 대기 시간을 줄일 수 있다.
  - 또한, 서버는 클라이언트가 필요로 할 리소스를 미리 알고 있기 때문에, 불필요한 요청을 줄일 수 있습니다.

<br />
<br />

## 👨🏻‍💻 HTTP/2.0과 HTTP/3.0 차이점

### 1. 전송 방식

<img width="482" alt="스크린샷 2023-03-20 오후 3 02 11" src="https://user-images.githubusercontent.com/64779472/226259589-83e35445-7874-4d04-9f83-6a9946e8082a.png">

- HTTP/2.0과 3.0의 대표적인 차이로 전송 방식에서 차이가 있다. HTTP/2.0은 `TCP`를 기반으로 동작하지만. HTTP/3.0은 `QUIC(Quick UDP Internet Connections)` 프로토콜을 사용한다.
- QUIC은 `UDP(User Datagram Protocol)`를 기반으로 하며, `TLS 보안 프로토콜`을 내장하고 있어 데이터의 암호화와 복호화를 더욱 강화했다. 이를 통해 서버와 클라이언트 간의 통신이 더욱 빠르고 안전하게 이루어집니다.

<br />

### 2. 헤더 압축

- HTTP/2.0은 `HPACK 압축 알고리즘`을 사용하여 헤더를 압축하지만, HTTP/3.0은 `QPACK 압축 알고리즘`을 사용한다. QPACK은 HPACK과 유사하지만, 더욱 효율적인 압축을 제공한다.

<br />

### 3. 무결성 검사

- HTTP/3.0에서는 `QUIC의 특성`을 활용하여 데이터 무결성을 검사하기 위해 `크기가 작은 패킷`을 사용한다.
- 이렇게 함으로써 데이터 무결성 검사를 보다 쉽게 수행할 수 있습니다. 이는 더 나은 성능과 안정성을 제공하며, 사용자 경험을 향상시키는 데 도움이 된다.

<br />

### 4. 지연 시간 감소

<img width="647" alt="스크린샷 2023-03-20 오후 3 08 46" src="https://user-images.githubusercontent.com/64779472/226260504-4b1cf52d-de3d-4baf-ad8c-f4b772cb260c.png">

- HTTP/3.0의 QUIC 프로토콜은 `UDP기반`으로 동작하고, UDP는 TCP와 달리 `연결 설정(3-way handshake)` 및 `해제 과정(4-way handshake)`을 필요로 하지 않기 때문에, 지연 시간이 감소하고 통신 속도가 빨라진다.
- 참고로, QUIC라고 해서 handshake를 완전히 하지 않는 것은 아니다. 3-way-handshake, 4-way-handshake 대신 `1-RTT(One Round Trip Time)` handshake를 사용한다.
- 1-RTT handshake는 초기에 클라이언트와 서버 간의 통신을 설정할 때 `한 번의 왕복 시간`만을 사용하여 handshake를 수행한다는 것을 의미합니다.
  - 이를 위해 클라이언트는 요청과 함께 `암호화된 연결 설정 정보`를 서버로 전송하고, 서버는 이 정보를 사용하여 클라이언트와의 연결을 설정합니다.

<br />