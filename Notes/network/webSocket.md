# 웹소켓(WebSocket)

## 웹소켓(WebSocket)

</br>

### 배경

과거에는 데이터를 가져오려면 **URL을 통한 요청이 필요**했고, 이로 인해 중복 데이터 전송과 페이지 새로고침이 필요했다. `Ajax`는 클라이언트에서 서버로 데이터를 비동기적으로 요청하여 **페이지 전체를 새로 고치지 않고 일부 정보를 업데이트**할 수 있게 해주었다.

그러나 Ajax도 여전히 HTTP를 사용하며, 데이터를 가져오려면 버튼을 누르거나 주기적으로 요청을 보내야 하므로 번거롭고 자원을 낭비한다. `웹소켓`은 이러한 문제를 해결하기 위한 기술로, **실시간 데이터를 효율적으로 가져올 수 있게 해주는 것이다.**

</br>
</br>

### 개념

Transport protocol의 일종으로 서버와 클라이언트 간의 효율적인 양방향 통신을 실현하기 위한 구조다.

웹소켓은 단순한 API로 구성되어있으며, 웹소켓을 이용하면 하나의 HTTP 접속으로 양방향 메시지를 자유롭게 주고받을 수 있다.

과거에는 웹에서 서버로 데이터를 받기 위해서는 클라이언트(브라우저)가 요청을 보내야 했다. 그러나 웹소켓은 이런 문제를 해결하는 새로운 방법을 제공한다.

웹소켓은 서버와 **브라우저 간에 양방향 통신이 가능하게 해주는 기술**이다. 이를 통해 브라우저는 서버가 직접 데이터를 보내주기 때문에 사용자가 웹 페이지를 새로고침하거나 다른 페이지로 이동하지 않아도 실시간으로 데이터를 받아볼 수 있다. 이로써 웹 어플리케이션에서 채팅, 게임, 주식 차트 등과 같이 실시간 업데이트가 필요한 기능을 효과적으로 개발할 수 있게 되었다.

</br>
</br>

### 작동원리

![](https://velog.velcdn.com/images/sju4486/post/5bb9bd84-df0c-4ae6-98cd-0e21ac820192/image.png)

웹소켓은 서버와 클라이언트 간의 실시간 통신을 가능하게 하는 기술이며, HTTP를 통한 연결을 설정한 후 실제 데이터 전송은 웹소켓을 통해 이루어진다. 웹소켓은 서버와 클라이언트 간에 양방향 통신을 열어주며, 연결은 일정 시간 후 자동으로 끊어진다. 더 복잡한 기능을 위해 `SockJS`나 `Socket.IO`와 같은 라이브러리를 사용하며, 데이터 통신에는 `STOMP`와 같은 프로토콜을 함께 활용한다.

</br>
</br>

### 웹 소켓 연결 과정

브라우저에서 소켓 통신을 이용하기 위해서는 소켓 통신이 가능한지 확인하는 **핸드셰이크(Hand Shake)** 과정이 필요하다.

- 브라우저에서 HTTP 통신을 이용하여 서버에 소켓 통신이 가능한지 요청을 보낸다. 이 때 헤더에 소켓을 사용하기 위한 `Upgrade`, `Connection`, `WebSocket`에 관한 정보를 함께 전송한다.

```
GET /chat
Host: https://chanstory.dev
Origin: https://chanstory.dev
Connection: Upgrade
Upgrade: websocket
Sec-WebSocket-Key: ...
Sec-WebSocket-Version: 13
```

- 서버에서 웹 소켓 통신이 가능하다면 서버에서 웹 소켓 통신이 가능하다는 `101 상태`의 응답을 보낸다. 이 때 서버에서는 클라이언트에서 받은 `'Sec-WebSocket-Key'` 키 값에 문자를 더한 뒤 암호화하여 `'Sec-WebSocket-Accept'`로 클라이언트로 응답한다.

```
101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: ...
```

이 프로토콜 스위칭 과정은 웹 소켓 라이브러리`Socket.io`에서 내부적으로 처리되므로 일반적인 개발자가 직접 다루지 않아도 된다. 웹 소켓 라이브러리는 HTTP에서 웹 소켓으로의 프로토콜 스위칭 및 웹 소켓 핸드셰이크 과정을 처리하고, 이후에는 웹 소켓을 사용하여 양방향 통신을 가능하게 한다.

따라서 개발자는 웹 소켓 라이브러리`Socket.io`를 사용하여 더 편리하게 웹 소켓 통신을 구현할 수 있고, 클라이언트와 서버 사이의 프로토콜 스위칭 및 웹 소켓 핸드셰이크 과정을 걱정하지 않아도 된다. `Socket.io`는 이러한 복잡한 세부 사항을 내부적으로 처리하므로 개발자는 웹 소켓을 더 쉽게 사용할 수 있다.

### 문제점

- 프로그램 구현에 보다 많은 복잡성
- 서버와 클라이언트 간의 Socket 연결을 유지하는 비용
- 오래된 버전의 웹 브라우저에서는 지원하지 않는다.

## 채팅기능

`HTML 파일`

```
<!DOCTYPE html>
<html>
<head>
    <title>채팅</title>
</head>
<body>
    <div id="chat">
        <div id="chat-messages"></div>
        <input type="text" id="message" placeholder="메시지 입력" />
        <button id="send">전송</button>
    </div>

    <!-- 웹 소켓 라이브러리 포함 -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/4.1.3/socket.io.js"></script>
    <!-- 클라이언트 스크립트 포함 -->
    <script src="chat.js"></script>
</body>
</html>
```

`chat.js`

- 클라이언트 측 JavaScript 파일

```jsx
document.addEventListener("DOMContentLoaded", () => {
  const socket = io(); // 서버와 소켓 연결

  const messageInput = document.getElementById("message");
  const sendButton = document.getElementById("send");
  const messageContainer = document.getElementById("chat-messages");

  // 서버로 메시지 보내기
  sendButton.addEventListener("click", () => {
    const message = messageInput.value;
    if (message) {
      socket.emit("chat message", message);
      messageInput.value = "";
    }
  });

  // 서버에서 메시지 받기
  socket.on("chat message", (message) => {
    const messageElement = document.createElement("div");
    messageElement.textContent = message;
    messageContainer.appendChild(messageElement);
  });
});
```

`server.js`

- Node.js 서버 파일

```jsx
const express = require("express");
const http = require("http");
const socketIo = require("socket.io");

const app = express();
const server = http.createServer(app);
const io = socketIo(server);

app.get("/", (req, res) => {
  res.sendFile(__dirname + "/index.html");
});

io.on("connection", (socket) => {
  console.log("사용자가 연결되었습니다.");

  // 클라이언트로부터 메시지 받기
  socket.on("chat message", (message) => {
    console.log(`메시지 받음: ${message}`);

    // 모든 클라이언트에게 메시지 전송
    io.emit("chat message", message);
  });

  socket.on("disconnect", () => {
    console.log("사용자가 연결 해제되었습니다.");
  });
});

server.listen(3000, () => {
  console.log("서버가 3000 포트에서 실행 중입니다.");
});
```

## 참고

- https://ko.javascript.info/websocket
- https://www.chanstory.dev/blog/post/26
- https://choseongho93.tistory.com/266
