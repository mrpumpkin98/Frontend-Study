# Lifecycle

## 함수형 컴포넌트 생명주기(lifecycle)

React의 라이프사이클은 컴포넌트가 생성되고 업데이트되며 소멸하는 과정을 다루는 개념

## React 컴포넌트의 라이프사이클의 세 단계

![](https://velog.velcdn.com/images/sju4486/post/843e33da-143f-42f0-9762-15936785188c/image.png)

**1. 생성 (Mounting)**

- 컴포넌트가 처음으로 생성될 때의 단계
- 주로 `constructor`, `render`, `componentDidMount` 메서드가 실행
  > 1.  `constructor` : 컴포넌트의 초기 설정과 상태를 설정(컴포넌트가 만들어지면 가장 먼저 실행)
  > 2.  `render` : UI를 생성하고 반환
  > 3.  `componentDidMount` : 컴포넌트가 화면에 나타난 직후, 데이터를 불러오거나 초기화 작업을 수행(컴포넌트 첫 렌더링을 마친 후 호출되는 메서드 이 단계에선 axios, fetch 등을 사용해 해당 컴포넌트에서 필요하는 데이터를 요청)

**2. 업데이트 (Updating)**

- 컴포넌트의 상태나 속성이 변경되면 이 단계로 진입
- 주로 `shouldComponentUpdate`, `render`, `componentDidUpdate` 메서드가 실행
  > 1.  `shouldComponentUpdate` : 컴포넌트가 리렌더링할 필요가 있는지 판단(React.memo와 역할이 비슷)
  > 2.  `render` : 변경된 데이터를 바탕으로 UI를 업데이트
  > 3.  `componentDidUpdate` : 업데이트가 완료된 후 추가 작업을 수행(리렌더링을 마친 후 브라우저에 호출되는 메서드)

**3. 소멸 (Unmounting)**

- 컴포넌트가 제거될 때의 단계
- 주로 `componentWillUnmount` 메서드가 실행
  > 1.  `componentWillUnmount` : 컴포넌트가 제거되기 전에 정리 작업을 수행(DOM에 직접 등록했던 이벤트를 제거)

## 참고

- https://velog.io/@minbr0ther/React.js-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4life-cycle-%EC%88%9C%EC%84%9C-%EC%97%AD%ED%95%A0
- https://ko.legacy.reactjs.org/docs/state-and-lifecycle.html
- https://www.zerocho.com/category/React/post/579b5ec26958781500ed9955
- https://whwl.tistory.com/282
