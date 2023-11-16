# Props Drilling 과 Key Props

## Props Drilling

`Props drilling`은 React 애플리케이션에서 상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달하는 과정을 나타낸다. 이는 중첩된 컴포넌트 구조에서 특히 발생하며, 데이터를 하위 컴포넌트로 전달하려면 중간에 있는 여러 컴포넌트를 통과해야 한다. 이러한 과정은 때로는 불필요한 코드 복잡성과 유지보수의 어려움을 초래할 수 있다.

```jsx
// GrandparentComponent.js
import React, { useState } from "react";
import ParentComponent from "./ParentComponent";

function GrandparentComponent() {
  const [data, setData] = useState("Hello from Grandparent");

  return (
    <div>
      <h1>{data}</h1>
      <ParentComponent data={data} />
    </div>
  );
}

// ParentComponent.js
import React from "react";
import ChildComponent from "./ChildComponent";

function ParentComponent({ data }) {
  return (
    <div>
      <h2>{data}</h2>
      <ChildComponent data={data} />
    </div>
  );
}

// ChildComponent.js
import React from "react";

function ChildComponent({ data }) {
  return (
    <div>
      <h3>{data}</h3>
    </div>
  );
}

export default ChildComponent;
```

### Props Drilling 해결

Props Drilling의 문제를 해결하려면 컴포넌트 간에 데이터를 전달하는 방식을 개선하거나, 전역 상태 관리를 도입하는 방법을 고려할 수 있다.

## Key Props

**`key`** 속성은 React에서 컴포넌트 배열을 렌더링할 때 각 항목에 고유한 식별자를 제공하는 데 사용된다. **`key`** 를 사용하면 React가 컴포넌트의 상태를 유지하고 업데이트할 때 효율적으로 작동할 수 있다.

### 성능 최적화

- **`key`** 를 지정하면 React가 이전과 현재의 엘리먼트를 빠르게 비교할 수 있다. 고유한 **`key`** 가 있으면 React는 어떤 엘리먼트가 추가, 업데이트, 또는 제거되었는지를 효과적으로 파악할 수 있다.
- **`key`** 를 사용하지 않으면 React는 각 엘리먼트를 비교할 때마다 전체 리스트를 탐색해야 하므로 성능이 저하될 수 있다.

### 컴포넌트 상태의 유지

- **`key`** 를 사용하면 React가 컴포넌트의 상태를 효과적으로 유지할 수 있다. 만약 **`key`** 가 없다면, 배열의 순서가 변경되거나 항목이 추가/제거될 때마다 React는 각 컴포넌트를 완전히 재생성하게 되어 상태가 유지되지 않는다.

### React의 내부 알고리즘 활용

- **`key`** 를 사용하면 React가 효율적인 업데이트 알고리즘을 사용할 수 있다. 예를 들어, 키가 있는 경우 React는 키를 기준으로 엘리먼트를 매핑하여 변경된 부분만 업데이트하게 된다.

### 동적인 엘리먼트에 대한 안정성

- 동적으로 생성되는 엘리먼트나 컴포넌트에 **`key`** 를 제공하면 React는 이를 통해 안정성을 유지할 수 있다. 특히 동적으로 생성되는 엘리먼트는 **`key`** 가 없을 경우 예상치 못한 문제가 발생할 수 있다.

key는 일반적으로 고유하고 안정적인 값을 사용하는 것이 좋다. 배열의 index를 key로 사용하는 것은 피하는 것이 좋다. 고유성이 보장되지 않으며 배열의 순서가 변경될 때 문제가 발생할 수 있기 때문이다.
