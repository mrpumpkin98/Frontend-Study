# BOM 과 DOM

## BOM(Browser Object Model)

![](https://velog.velcdn.com/images/sju4486/post/e2f90e11-2086-46e8-ab6b-798c558dd90d/image.png)

- **웹 브라우저와 관련된 객체의 집합**
- 객체 모델 종류: `window`(최상위), `location`, `navigator`, `history`, `screen`, `document`
- DOM(Document Object Model) 으로 통합해서 칭하기도 함
- 정확히는 자바스크립트가 아닌 **웹브라우저가 제공하는 기능**

### window 객체

다른 **BOM 객체의 상위 개념**
`alert()`, `prompt()` 등 많은 메소드를 가지고 있음
var 키워드로 선언한 일반 변수도 window 객체의 속성이 됨
window 객체 생성 메소드 : open(URL, name, features, replaced)

> 💡 객체 생성시 생성한 객체를 반환하기 때문에 변수에 입력해서 자유롭게 수정 가능
> ex) var newWin = window.open();

- `open(url,windowName[,option])` : 새 창을 열 때 사용
- `alert()` : 경고 창을 띄움
- `prompt()` : 질의 응답 창을 띄움
- `confirm()` : 확인 / 취소 창을 띄움
- `moveTo(x,y)` : 창의 위치를 이동시킬 때 사용
- `resizeTo(width,height)` : 창의 크기를 변경시킬 때 사용
- `setInterval(function, millseconds)` : 일정 간격으로 지속적으로 실행문을 실행 시킬 때 사용
- `setTimeout(function, milliseconds)` : 일정 간격으로 한 번만 실행문을 실행 시킬 때 사용

### screen 객체

웹브라우저 화면이 아닌 운영체제 화면의 속성을 갖는 객체

- `screen.width` : 화면의 너빗값을 반환
- `screen.height` : 화면의 높잇값을 반환
- `screen.availWidth` : 작업 표시줄을 제외한 화면의 너빗값 반환
- `screen.availHeight` : 작업 표시줄을 제외한 화면의 높잇값을 반환
- `screen.colorDepth` : 사용자 모니터가 표현 가능한 컬러 bit를 반환

### location 객체

웹브라우저의 주소 표시줄과 관련된 객체
location 객체는 **프로토콜의 종류, 호스트 명, 문서 위치** 등의 정보가 있음

- `location.href` : 주소 영역에 참조 주소를 설정하거나 url을 반환
- `location.hash` : url에 해시값(#에 명시된 값)을 반환
- `location.hostname` : url에 호스트 이름을 설정하거나 반환
- `location.host` : url에 호스트 이름과 포트 번호를 반환
- `location.port` : url에 포트 번호를 반환
- `location.protocol` : url에 프로토콜을 반환
- `location.search` : url에 쿼리(요청 값)를 반환
- `location.reload()` : 새로 고침

### navigator 객체

웹페이지를 실행 중인 브라우저에 대한 정보가 담긴 객체

- `navigator.appCodeName` : 방문자의 브라우저 코드명을 반환
- `navigator.appName` : 방문자의 브라우저 이름을 반환
- `navigator.appVersion` : 방문자의 브라우저 버전 정보를 반환
- `navigator.language` : 방문자의 브라우저 사용 언어를 반환
- `navigator.product` : 방문자의 브라우저 사용 엔진 이름 반환
- `navigator.platform` : 방문자의 브라우저를 실행하는 운영체제를 반환
- `navigator.userAgent` : 방문자의 브라우저와 운영체제 종합 정보를 제공

### history 객체

사용자가 방문한 사이트 중 이전에 방문한 사이트와 다음 방문한 사이트로 다시 돌아갈 수 있는 속성과 메서드를 제공

- `history.back()` : 이전 방문한 페이지로 이동
- `history.forward()` : 다음 방문한 페이지로 이동
- `history.go(이동 숫자)` : 이동 숫자가 -2 이면 2단계 이전 페이지로 이동
- `history.length` : 방문 기록에 저장된 목록의 개수를 반환

## DOM (Document Object Model)

![](https://velog.velcdn.com/images/sju4486/post/06713bcc-6691-416c-b42e-a51d0e19f2ef/image.png)

DOM은 **문서 객체 모델(Document Object Model)** 의 약자로, 웹 페이지의 구조를 프로그래밍적으로 조작하고 제어하기 위한 방법을 제공하는 중요한 웹 기술이다.

- **`문서(Document)`** : DOM은 웹 페이지를 문서로 간주한다. 이 문서는 HTML(하이퍼텍스트 마크업 언어)로 작성되며, 웹 페이지의 모든 내용을 포함하고 있다.

- **`객체(Object)`** : DOM은 문서를 객체의 집합으로 표현한다. 이러한 객체들은 웹 페이지의 각 요소를 나타내며, 예를 들어 HTML 태그, 텍스트, 이미지, 링크 등이 이 객체들로 표현된다.

- **`모델(Model)`** : DOM은 이 객체들을 계층적인 트리 구조로 나열한다. 이 트리 구조를 통해 웹 페이지의 계층적인 구조를 반영하며, 부모 요소와 자식 요소로 구성된다.

- **`프로그래밍적인 조작`** : 개발자들은 JavaScript와 같은 프로그래밍 언어를 사용하여 DOM 객체를 선택하고 수정할 수 있다. 이를 통해 웹 페이지의 내용, 스타일, 동작 등을 동적으로 변경할 수 있다.

**`HTML 문서`**

```
<!DOCTYPE html>
<html>
<head>
    <title>나의 웹 페이지</title>
</head>
<body>
    <h1>안녕하세요!</h1>
    <p>이것은 간단한 웹 페이지입니다.</p>
</body>
</html>
```

**`계층적인 구조`**

```
- 문서 (Document)
  - html 요소 (HTML element)
    - head 요소 (Head element)
      - title 요소 (Title element)
        - "나의 웹 페이지" 텍스트 노드
    - body 요소 (Body element)
      - h1 요소 (Heading element)
        - "안녕하세요!" 텍스트 노드
      - p 요소 (Paragraph element)
        - "이것은 간단한 웹 페이지입니다." 텍스트 노드
```

DOM은 웹 애플리케이션과 **웹 페이지의 상호작용을 가능하게 하는 핵심적인 기술로, 동적 웹 페이지를 구현하는 데 필수적**입니다.

## 참고

- https://wickies.tistory.com/26
- https://velog.io/@hih0327/12.-JavaScript-BOM
- http://www.tcpschool.com/javascript/js_dom_concept
- https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction
