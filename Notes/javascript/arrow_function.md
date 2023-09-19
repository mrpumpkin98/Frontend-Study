## 화살표 함수

화살표 함수(arrow function)는 JavaScript에서 함수를 정의하는 또 다른 방법 중 하나다. ES6(ECMAScript 2015)에서 도입되었으며, 함수를 더 간결하게 작성할 수 있다.

#### 예시

```jsx
// 기존 함수 표현식
const add = function (a, b) {
  return a + b;
};

// 화살표 함수로 변환
const addArrow = (a, b) => a + b;

// 화살표 함수로 변환 (중괄호 사용)
const greet = (name) => {
  return `Hello, ${name}!`;
};
```

#### 화살표 함수의 주요 특징

- **`간결함`** : 간단한 함수를 더 간결하게 작성할 수 있다.

- **`익명 함수`** : 주로 익명 함수로 사용되므로, 콜백 함수 등을 간결하게 표현할 수 있다.

- **`this 컨텍스트`** : 화살표 함수는 자신만의 this 컨텍스트를 가지지 않고, 외부 함수의 this를 상속받는다. 이로써 함수 내부에서 this를 사용할 때 발생하는 오류를 방지할 수 있다.

**[ 일반 함수 ]**

```jsx
function sayHello() {
  console.log("안녕하세요, " + this.name + "!");
}

const person = {
  name: "Alice",
  speak: sayHello,
};

person.speak(); // "안녕하세요, Alice!" 출력
```

일반 함수 `sayHello`는 자신의 `this` 컨텍스트를 생성하며, `person.speak()`를 호출할 때 `this`는 `person` 객체를 가리키게 된다.

**[ 화살표 함수 ]**

```jsx
const sayHello = () => {
  console.log("안녕하세요, " + this.name + "!");
};

const person = {
  name: "Alice",
  speak: sayHello,
};

person.speak(); // "안녕하세요, undefined!" 출력
```

화살표 함수 `sayHello`는 자신만의 `this`를 만들지 않고, 대신 외부 함수인 `person.speak`에서 상속받은 `this`를 사용한다. 그래서 이 경우 `this.name`은 `undefined`가 되고, 오류가 발생하지 않는다. 이렇게 화살표 함수는 `this` 오류를 방지하는데 도움이 된다.

## 참고

- https://poiemaweb.com/es6-arrow-function
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Arrow_functions
