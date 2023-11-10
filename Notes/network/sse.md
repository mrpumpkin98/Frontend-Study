# SSE

## SSE란 ?

SEE는 웹 어플리케이션, '서버에서 클라이언트'로 '단방향'으로 '실시간' 이벤트를 전송하는 '웹' 기술이다. SEE는 단방향 통신 방식으로 서버에서 클라이언트로 데이터를 전송한다.
![](https://velog.velcdn.com/images/sju4486/post/f383da88-95f8-4e7e-a38f-ec6b70dfa399/image.png)

## SSE의 특징

- **단방향 통신 :** SSE는 서버에서 클라이언트로 데이터를 보내는 단방향 통신 방식이다. 이것은 클라이언트가 서버에 요청을 보내지 않고도 서버가 데이터를 클라이언트로 보낼 수 있음을 의미한다.

- **텍스트 기반 :** SSE는 텍스트 데이터를 주로 전송한다. 이는 주로 JSON 형식 또는 다른 텍스트 기반 데이터 형식을 사용하여 정보를 클라이언트로 보내는 데 사용된다.

- **이벤트 기반 :** SSE는 이벤트 기반으로 작동하며, 서버는 클라이언트로 이벤트 메시지를 보낸다. 클라이언트는 이벤트 메시지를 수신하고 처리할 수 있으며, 이벤트 이름과 데이터를 포함한다.

- **데이터 스트림 :** SSE는 데이터를 스트림으로 전송하므로, 서버가 주기적으로 데이터를 보내는 동안 클라이언트는 연결을 유지하고 데이터를 실시간으로 수신할 수 있다.

- **간단한 구현 :** SSE는 웹 브라우저에서 내장된 표준 API를 사용하여 구현할 수 있으므로, 간단한 서버 및 클라이언트 코드로 쉽게 사용할 수 있다.

## SSE와 웹소켓 차이점

SSE와 WebSocket은 웹 애플리케이션의 실시간 통신을 지원하는 기술이지만 중요한 차이점이 있다.

SSE는 단방향 통신으로, 서버에서 클라이언트로 데이터를 푸시하고 HTTP 프로토콜 위에서 동작한다. 주로 단방향 데이터 스트리밍을 위해 사용되고 주기적인 업데이트를 제공하는 데 유용하다. 반면 WebSocket은 양방향 통신을 지원하고 WebSocket 프로토콜을 사용하여 데이터를 주고받으므로 양방향 통신 및 실시간 상호작용에 적합하다. **SSE는 주로 서버에서 클라이언트로 데이터 푸시에 사용**되고, **WebSocket은 실시간 채팅, 온라인 게임 등의 상호작용 기능에 사용**된다.

![](https://velog.velcdn.com/images/sju4486/post/2b4bb295-dd6c-425b-8d5c-bbac24283ef2/image.png)

## SSE와 폴링 차이점

폴링과 SSE는 웹 애플리케이션에서 서버와의 통신 방식을 다르게 다루는 기술이다. 폴링은 클라이언트가 주기적으로 서버에 데이터를 요청하고 데이터 업데이트를 확인하는 방식으로, 업데이트에 대한 지연과 불필요한 트래픽을 초래할 수 있다. 반면 SSE는 서버에서 클라이언트로 데이터를 주기적으로 푸시하므로 실시간 업데이트가 가능하며, 클라이언트는 요청을 보내지 않고 데이터를 수신한다. SSE는 실시간 업데이트와 데이터의 실시간 푸시에 효과적이며, 구현이 간단한 장점을 가진다.

## SSE 사용해보기

**`데이터 포멧`**

```js
id: testN1\n
event: red\n
data: {"message" : "hello SSE!", "text" : "blah-blah"}\n\n
```

**`server.js`**

```js
// 먼저 해더를 아래와 같이 보내야 한다.
const headers = {
  "Content-Type": "text/event-stream",
  Connection: "keep-alive",
  "Cache-Control": "no-cache",
};
```

```js
res.writeHead(200, headers);

const clientId = request.query.clientId;
clients[clientId] = {
  response,
};
request.on("close", () => {
  delete clients[clientId];
});
```

```js
// 이제 서버에서 어떤 이벤트가 발생 했을 때 데이터 클라이언트로 보내기
// 예시 서버 최초 9+ 강화 성공
const notifyUser = (req, res) => {
  const payload = {...}
  clients.forEach(client =>
  	client.response.write(`data: ${JSON.stringify(payload)}\n\n`)
}
```

> 💡 **버퍼 없애기**
>
> HTTP header - X-Accel-Buffering: no </br>
> ngnix config - proxy_buffering off

**`client`**

```js
useEffect(() => {
  // 너와 나의 연결고리 만들어 주기
  const sseEvents = new EventSource("http://localhost:3000/sse");

  sseEvents.onopen = function () {
    // 연결 됐을 때
  };
  sseEvents.onerror = function (error) {
    // 에러 났을 때
  };
  sseEvents.onmessage = function (stream) {
    // 메세지 받았을 때
    const parsedData = JSON.parse(stream.data);
  };
}, []);
```

## 참고

- https://suzzeong.tistory.com/86
- [웹소켓 과 SSE(Server-Sent-Event) 차이점 알아보고 사용해보기](https://surviveasdev.tistory.com/entry/%EC%9B%B9%EC%86%8C%EC%BC%93-%EA%B3%BC-SSEServer-Sent-Event-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B3%A0-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0)
- https://lotuus.tistory.com/151
