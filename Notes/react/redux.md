# Redux

리덕스(Redux)는 JavaScript 애플리케이션의 상태 관리를 위한 예측 가능한(state predictable) 컨테이너 상태 관리 패턴과 라이브러리다. 리덕스는 주로 React와 함께 사용되며, React 외에도 Angular, Vue 등 다른 프레임워크와도 함께 사용할 수 있다.

리덕스(Redux)의 주요 목표는 애플리케이션의 상태 변화를 예측 가능하고 디버깅하기 쉽게 만들어 개발자들이 복잡한 상태 관리를 간편하게 할 수 있도록 하는 것이다. **상태를 중앙 집중화하여 관리함으로써 다양한 컴포넌트 간에 상태 공유가 가능하고, 애플리케이션의 복잡성을 줄일 수 있다.**

## ✅ 스토어(Store)

**애플리케이션의 상태를 저장하는 객체,** 리덕스 스토어는 애플리케이션의 상태를 단일 소스로 유지한다.

```tsx
import { createStore } from "redux";

// 초기 상태 정의
const initialState = {
  count: 0,
};

// 리듀서 함수 정의
function reducer(state = initialState, action) {
  switch (action.type) {
    case "INCREMENT":
      return {
        ...state,
        count: state.count + 1,
      };
    case "DECREMENT":
      return {
        ...state,
        count: state.count - 1,
      };
    default:
      return state;
  }
}

// 스토어 생성
const store = createStore(reducer);
```

## ✅ 액션(Action)

**상태를 변경하기 위한 정보를 나타내는 객체,** 액션은 반드시 type 필드를 가지고 있어야 하며, 필요에 따라 다른 데이터를 포함할 수도 있다.

```tsx
// 액션 타입 정의
const INCREMENT = "INCREMENT";
const DECREMENT = "DECREMENT";

// 액션 생성 함수 정의
function increment() {
  return { type: INCREMENT };
}

function decrement() {
  return { type: DECREMENT };
}

// 디스패치 예제
store.dispatch(increment());
store.dispatch(decrement());
```

## ✅ 리듀서(Reducer)

**액션과 이전 상태를 받아 새로운 상태를 반환하는 순수한 함수,** 리듀서는 애플리케이션의 상태를 변경하는 로직이 포함되어 있다.

```tsx
function reducer(state = initialState, action) {
  switch (action.type) {
    case "INCREMENT":
      return {
        ...state,
        count: state.count + 1,
      };
    case "DECREMENT":
      return {
        ...state,
        count: state.count - 1,
      };
    default:
      return state;
  }
}
```

## ✅ 선택자(Selector)

**상태에서 필요한 데이터를 추출하는 함수,** 선택자를 사용하여 필요한 데이터를 쉽게 가져올 수 있다.

```tsx
// 상태에서 필요한 데이터를 추출하는 선택자 함수
function getCount(state) {
  return state.count;
}

// 선택자 사용 예제
const currentState = store.getState();
const currentCount = getCount(currentState);
console.log(currentCount); // 상태에서 추출한 count 값 출력
```

## ✅ React redux 사용법

### ◾ store.js 생성

![](https://velog.velcdn.com/images/sju4486/post/32982768-d073-4461-84c2-7901ef585ab5/image.png)

</br>

### ◾store.js

![](https://velog.velcdn.com/images/sju4486/post/ecc0c4ea-abf7-45ae-8da4-de3df86f2744/image.png)

- **Action 만들기**

```tsx
export const plusStr = () => ({ type: "PLUS", str: "helloWorld" });
```

- **상태 객체 만들기**

```tsx
const initState = {
  str: "안녕하세요",
};
```

- **reducer 만들기**

```tsx
export const reducer = (state = initState, action) => {
  switch (action.type) {
    case "PLUS":
      return { str: state.str + state.str };
    default:
      return state;
  }
};
```

</br>

### ◾_app.js에서 Redux설정

```tsx
import { Provider } from "react-redux";
import { createStore } from "redux";
import reducer from "../src/commons/store"; // 리듀서 파일 경로

import Layout from "../src/commons/Layout/index";
import "../styles/globals.css";

// 루트 리듀서로 스토어 생성
const store = createStore(reducer);

export default function App({ Component, pageProps }) {
  return (
    <Provider store={store}>
      <Layout>
        <Component {...pageProps} />
      </Layout>
    </Provider>
  );
}
```

</br>

### ◾ useSelector 함수를 사용

```tsx
import Head from "next/head";
import { useSelector } from "react-redux";

export default function GraphqlMutationPage() {
  const str = useSelector((store) => store.str);
  return (
    <>
      <Head>
        <title>Redux</title>
      </Head>
      <h1>{str}</h1>
    </>
  );
}
```

</br>

### ◾ 초기화면

![](https://velog.velcdn.com/images/sju4486/post/dcecf548-94f3-4a27-ab35-1cb1ef9093e5/image.png)

## 📝 실습

**`store.js`**

```ts
import { createStore, combineReducers } from "redux";

// Action 생성 함수
export const setLoggedIn = () => {
  return {
    type: "SET_LOGGED_IN",
  };
};

export const setLoggedOut = () => {
  return {
    type: "SET_LOGGED_OUT",
  };
};

export const setCountUp = () => {
  return {
    type: "SET_COUNT_UP",
  };
};

export const setCountDown = () => {
  return {
    type: "SET_COUNT_DOWN",
  };
};

// 로그인 상태를 관리하는 Reducer
const authReducer = (state = { isLoggedIn: false }, action) => {
  switch (action.type) {
    case "SET_LOGGED_IN":
      return {
        ...state,
        isLoggedIn: true,
      };
    case "SET_LOGGED_OUT":
      return {
        ...state,
        isLoggedIn: false,
      };
    default:
      return state;
  }
};

const counter = (count = { isCounter: 0 }, action) => {
  switch (action.type) {
    case "SET_COUNT_UP":
      return {
        ...count,
        isCounter: count.isCounter + 1,
      };
    case "SET_COUNT_DOWN":
      return {
        ...count,
        isCounter: count.isCounter - 1,
      };
    default:
      return count;
  }
};

// 리듀서들을 합침
const rootReducer = combineReducers({
  auth: authReducer,
  counter: counter,
});

// 스토어 생성
const store = createStore(rootReducer);

export default store;
```

**`index.jsx`**

```tsx
import React from "react";
import { connect } from "react-redux";
import {
  setLoggedIn,
  setLoggedOut,
  setCountUp,
  setCountDown,
} from "../../commons/store";
import { useSelector, useDispatch } from "react-redux";
import styled from "@emotion/styled";

const Container = styled.div`
  max-width: 500px;
  margin: 100px auto;
  text-align: center;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
`;

const Title = styled.h1`
  font-size: 24px;
  text-align: center;
`;

const Button = styled.button`
  margin-right: 10px;
  padding: 10px 20px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: 20px;
  > &:hover {
    background-color: #45a049;
  }
`;

const SomeComponent = () => {
  const isLoggedIn = useSelector((state) => state.isLoggedIn);
  const isCounter = useSelector((count) => count.isCounter);

  const aa = useDispatch();
  const bb = useDispatch();
  const handleButtonClick = () => {
    aa(setLoggedIn()); // 로그인 액션 디스패치
  };

  const handleButtonClick2 = () => {
    aa(setLoggedOut()); // 로그아웃 액션 디스패치
  };

  const handleButtonClick3 = () => {
    bb(setCountUp());
  };

  const handleButtonClick4 = () => {
    bb(setCountDown());
  };

  const { auth, counter } = useSelector((aaa) => aaa); // aaa에 어떤 값이 들어와도 상관X
  return (
    <>
      <Container>
        <Title>로그인 상태 : {auth.isLoggedIn ? "Yes" : "No"}</Title>
        <Button onClick={handleButtonClick}>로그인</Button>
        <Button onClick={handleButtonClick2}>로그아웃</Button>
      </Container>
      <Container>
        <Title>카운터 : {counter.isCounter}</Title>
        <Button onClick={handleButtonClick3}>증가</Button>
        <Button onClick={handleButtonClick4}>감소</Button>
      </Container>
    </>
  );
};
export default SomeComponent;
```

</br>
</br>

![](https://velog.velcdn.com/images/sju4486/post/2576c9af-5a80-47e2-9151-b578367525c0/image.gif)
