# 모듈 시스템

## 모듈(module)이란?

모듈이란 여러 기능들에 관한 코드가 모여있는 하나의 파일 로 다음과 같은 것들을 위해 사용한다.

- **`유지보수성`** : 기능들이 모듈화가 잘 되어있다면, 의존성을 그만큼 줄일 수 있기 때문에 어떤 기능을 개선한다거나 수정할 때 훨씬 편하게 할 수 있다.
- **`네임스페이스화`** : 자바스크립트에서 전역변수는 전역공간을 가지기 때문에 코드의 양이 많아질수록 겹치는 네임스페이스가 많아질 수 있다. 그러나 모듈로 분리하면 모듈만의 네임스페이스를 갖기 때문에 그 문제가 해결된다.
- **`재사용성`** : 똑같은 코드를 반복하지 않고 모듈로 분리시켜서 필요할 때마다 사용할 수 있다.

## CommonJS

CommonJS는 JavaScript 모듈 시스템의 일부로, 주로 서버 측 JavaScript 환경에서 사용되는 모듈 시스템이다. CommonJS는 Node.js에서 널리 사용되며, 서버 측 백엔드 코드를 작성할 때 주로 활용된다. 이 시스템은 모듈화된 코드를 쉽게 작성하고 재사용할 수 있도록 도와준다.

**`모듈 정의`**

- CommonJS 모듈은 module.exports와 exports 객체를 사용하여 정의
- module.exports를 사용하여 모듈에서 내보낼 객체나 함수를 지정

```jsx
// 모듈 정의
module.exports = {
  greet: function (name) {
    return `Hello, ${name}!`;
  },
  // 다른 모듈에서 사용할 변수나 함수 등을 정의할 수 있습니다.
};
```

**`모듈 가져오기`**

- 다른 모듈에서 CommonJS 모듈을 가져오려면 require() 함수를 사용

```jsx
// main.js
const myModule = require("./my-module");
console.log(myModule.greet("John")); // 출력: "Hello, John!"
```

## AMD

AMD(Asynchronous Module Definition)는 JavaScript 모듈 시스템의 한 형태로, **주로 브라우저 환경에서 사용**된다. AMD는 모듈을 비동기적으로 로드하고 정의할 수 있는 기능을 제공하여 웹 애플리케이션의 성능을 향상시키는 데 도움이 된다.

**`모듈 정의`**

- AMD 모듈은 `define` 함수를 사용하여 정의된다. 이 함수는 모듈의 **종속성**(dependencies)과 **모듈 내용**(factory function)을 정의한다.

```jsx
define(["dependency1", "dependency2"], function (dep1, dep2) {
  // 모듈 내용을 정의합니다.
  return {
    someFunction: function () {
      // 모듈 기능을 정의합니다.
    },
  };
});
```

**`모듈 가져오기`**

- 다른 모듈에서 AMD 모듈을 가져오려면 require 함수를 사용한다. 모듈의 종속성은 자동으로 로드되고 콜백 함수가 호출된다.

```jsx
require(["myModule"], function (myModule) {
  myModule.someFunction();
});
```

> 💡 **비동기 로딩**
>
> - AMD 모듈 시스템은 모듈을 비동기적으로 로드하므로 페이지 로딩 성능을 향상시킬 수 있다. 필요한 모듈만 로드되고 사용된다.

## UMD

UMD(Universal Module Definition)는 J**avaScript 모듈을 여러 환경에서 사용할 수 있도록 만든 형식 중 하나**다. UMD는 모듈을 브라우저 환경, Node.js 등 다양한 환경에서 사용할 수 있도록 설계되어 있으며, **CommonJS** 및 **AMD** 모듈 시스템과 **호환성**을 가지고 있다.

**`모듈 정의`**

- UMD 모듈은 자체 실행 가능한 함수로 정의된다. 이 함수는 브라우저 환경에서 전역 객체(window)에 모듈을 노출하거나 Node.js 환경에서 exports 객체에 모듈을 할당한다.

```jsx
(function (root, factory) {
  if (typeof define === "function" && define.amd) {
    // AMD 환경에서 모듈 정의
    define(["dependency1", "dependency2"], factory);
  } else if (typeof exports === "object") {
    // CommonJS(Node.js) 환경에서 모듈 정의
    module.exports = factory(require("dependency1"), require("dependency2"));
  } else {
    // 브라우저 환경에서 모듈 정의
    root.myModule = factory(root.dependency1, root.dependency2);
  }
})(typeof self !== "undefined" ? self : this, function (dep1, dep2) {
  // 모듈 내용을 정의
  return {
    someFunction: function () {
      // 모듈 기능을 정의
    },
  };
});
```

**`모듈 가져오기`**

- UMD 모듈을 사용할 때, 해당 모듈이 현재 환경에서 어떻게 사용 가능한지에 따라 다른 방식으로 가져올 수 있다. 브라우저에서는 전역 객체를 통해 모듈에 접근하고, **CommonJS**나 **AMD** 환경에서는 각각의 방식으로 가져올 수 있다.

```jsx
// 브라우저 환경에서 사용
myModule.someFunction();

// CommonJS(Node.js) 환경에서 사용
const myModule = require("myModule");
myModule.someFunction();

// AMD 환경에서 사용
require(["myModule"], function (myModule) {
  myModule.someFunction();
});
```

## ES6(ES2015)

- ES6(ECMAScript 2015) 모듈 시스템은 JavaScript의 표준 모듈 시스템으로, 브라우저 및 Node.js와 같은 환경에서 사용할 수 있다. ES6 모듈 시스템은 다른 모듈 시스템과 비교하여 더 간결하고 강력한 모듈 기능을 제공한다.

**`모듈 정의`**

- ES6 모듈은 **export** 및 **import** 키워드를 사용하여 정의된다.
- **export** 키워드를 사용하여 모듈에서 외부로 내보낼 항목을 지정한다.

```jsx
// 모듈 정의
export function add(a, b) {
  return a + b;
}

export const pi = 3.14159265359;
```

**`모듈 가져오기`**

- 다른 모듈에서 ES6 모듈을 가져오려면 **import** 키워드를 사용한다.

```jsx
/ 모듈 가져오기
import { add, pi } from './my-module';
>
console.log(add(1, 2)); // 출력: 3
console.log(pi); // 출력: 3.14159265359
```

> 💡 ES6 모듈은 현대 JavaScript 개발에서 표준적인 방식으로 모듈을 작성하고 사용하는 데 권장된다.

## 참고

- https://ko.javascript.info/modules-intro#ref-300
- https://www.zerocho.com/category/JavaScript/post/5b67e7847bbbd3001b43fd73
