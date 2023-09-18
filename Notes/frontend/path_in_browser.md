# 브라우저의 렌더링 원리

브라우저가 화면에 나타나는 요소를 렌더링 할 때, **웹킷(Webkit)** 이나 **게코(Gecko)** 등과 같은 렌더링 엔진 을 사용한다. 렌더링 엔진이 HTML, CSS, Javascript로 렌더링할 때 **CRP(Critical Rendering Path)** 라는 프로세스를 사용하며 CRP는 아래와 같이 6단계로 구성

![](https://velog.velcdn.com/images/sju4486/post/266cbbb3-5246-493b-afd8-21a7f4129527/image.png)

- **`DOM 트리 구축`**(Constructing the DOM Tree)
- **`CSSOM 트리 구축`**(Constructing the CSSOM Tree)
- **`JavaScript 실행`**(Running JavaScript)
- **`랜더링 트리 구축`**(Creating the Render Tree)
- **`레이아웃 생성`**(Generating the Layout)
- **`페인팅`**(Painting)

> 💡 **`렌더링 트리`** 는 DOM과 CSSOM의 조합이다. 페이지에서 최종적으로 렌더링 될 내용을 나타내는 트리다. 즉, 표시되는 내용만 캡쳐하가 때문에 `display:none` 을 사용하여 CSS로 숨겨진 요소는 포함하지 않는다.

아래 로그를 보면 알 수 있는 것처럼 위에서 언급한 CRP가 진행된다.

![](https://velog.velcdn.com/images/sju4486/post/5898fc8f-4c9e-4f7c-9d05-8034b1bb294b/image.png)

- Parse HTML을 통해 HTML 파싱 후, **DOM 트리 구축**
- Parse Stylesheet를 통해 CSS 파싱 후, **CSSOM 트리 구축**
- Evaluate Script를 통해 **Javascript 실행**
- **렌더트리 구축**
- Layout을 통해 뷰포트 기준으로 렌더트리 **노드들의 각 크기/위치 계산**
- Paint를 통해 Layout에서 계산한 값들로 **각 요소를 화면에 그림**

### 참고

- https://blog.asamaru.net/2017/05/04/understanding-the-critical-rendering-path
- https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/browser-rendering.md
