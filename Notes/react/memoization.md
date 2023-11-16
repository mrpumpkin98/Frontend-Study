# 메모이제이션

React에서 메모이제이션은 성능을 최적화하고 함수나 컴포넌트의 불필요한 계산을 피하기 위해 사용된다. 주로 `React.memo`, `useMemo`, `useCallback` 과 같은 React Hooks를 통해 메모이제이션을 활용할 수 있다.

## React.memo를 사용한 컴포넌트 메모이제이션

`React.memo` 는 함수형 컴포넌트를 메모이제이션하는 데 사용된다. 이를 통해 컴포넌트의 props가 변경되지 않으면 리렌더링을 방지할 수 있다.

```jsx
import React from "react";

const MyComponent = React.memo(({ prop1, prop2 }) => {
  // 컴포넌트 로직
});

// 사용 예시
<MyComponent prop1={value1} prop2={value2} />;
```

## useMemo를 사용한 값 메모이제이션

`useMemo` 는 계산 비용이 높은 값을 메모이제이션하여, 의존성 배열에 지정된 값들이 변경될 때에만 재계산한다.

```jsx
import React, { useMemo } from "react";

const MyComponent = ({ prop1, prop2 }) => {
  const memoizedValue = useMemo(() => {
    // prop1 또는 prop2를 사용한 계산
    return calculatedValue;
  }, [prop1, prop2]);

  // 컴포넌트 로직
};
```

## useCallback을 사용한 콜백 메모이제이션

`useCallback` 은 함수를 메모이제이션하여, 의존성 배열에 지정된 값들이 변경될 때에만 새로운 함수를 생성한다. 주로 자식 컴포넌트에 콜백 함수를 전달할 때 사용된다.

```jsx
import React, { useCallback } from "react";

const MyComponent = ({ onClick }) => {
  const handleClick = useCallback(
    () => {
      // 클릭 핸들러 로직
    },
    [
      /* 의존성 배열 */
    ]
  );

  // 컴포넌트 로직
};
```

## useCallback VS useMemo

`useCallback` 은 함수를 메모이제이션하여 콜백 함수의 불필요한 재생성을 방지하고, `useMemo` 는 값의 메모이제이션을 통해 계산 비용이 높은 연산의 성능을 최적화한다. 이 두 훅은 각각 다른 상황에서 사용되며, 성능 최적화에 도움이 된다.

## 주의

메모이제이션을 사용하면 렌더링 성능을 향상시키고 불필요한 계산을 방지할 수 있다. 그러나 의존성 배열에 모든 종속성을 나열해야 하며, 필요하지 않은 경우에는 메모이제이션을 사용하지 않는 것이 좋다. 메모이제이션은 성능 향상을 위한 도구이지만, 사용을 과도하게 하면 오히려 코드를 복잡하게 만들 수 있다.
