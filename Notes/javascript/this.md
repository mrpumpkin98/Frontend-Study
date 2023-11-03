# this

### 전역 범위에서의 `this` :

전역 범위에서 **`this`** 는 전역 객체인 **`window`** 를 가리킵니다. 브라우저 환경에서는 **`window`** 객체가 전역 범위에서 사용됩니다.

### 객체 메서드 내에서의 `this` :

객체 메서드 내에서 **`this`** 는 해당 메서드를 호출한 객체를 가리킵니다.

```jsx
const person = {
  name: "John",
  sayHello: function () {
    console.log(`안녕, 나는 ${this.name}이야.`);
  },
};

person.sayHello(); // "안녕, 나는 John이야."
```

### 화살표 함수에서의 `this` :

화살표 함수는 자체적인 **`this`** 컨텍스트를 가지지 않으며, 화살표 함수 내부에서 **`this`** 는 함수가 선언된 바깥 범위의 **`this`** 를 상속받습니다. 이것은 주변 함수나 메서드의 **`this`** 를 그대로 사용한다는 의미입니다. 다시 말하면, 화살표 함수 내에서 **`this`** 는 함수가 아닌 주변 범위의 **`this`** 를 가리키며, **`this`** 가 동적으로 바뀌지 않습니다.

```jsx
const person = {
  name: "John",
  sayHello: () => {
    console.log(`안녕, 나는 ${this.name}이야.`);
  },
};

person.sayHello(); // "안녕, 나는 undefined이야."
```

### `call`, `bind`, `apply`를 사용한 `this`의 변경 :

**`call`**, **`bind`**, **`apply`** 를 사용하여 함수의 **`this`** 를 명시적으로 변경할 수 있습니다. 이러한 메서드는 함수를 호출할 때 **`this`** 의 값을 변경하거나 인자를 전달합니다.

```jsx
function greet() {
  console.log(`안녕, 나는 ${this.name}이야.`);
}

const person1 = { name: "John" };
const person2 = { name: "Alice" };

greet.call(person1); // "안녕, 나는 John이야."
greet.call(person2); // "안녕, 나는 Alice이야."

const greetJohn = greet.bind(person1);
greetJohn(); // "안녕, 나는 John이야."
```

#### ⚙️ call 메서드

call 메서드는 함수를 호출하면서 this 값을 지정할 수 있습니다. 이 메서드는 함수 호출 시 첫 번째 매개변수로 전달된 객체를 this 값으로 설정합니다. 함수가 호출되면 this는 해당 객체를 참조하게 됩니다. 또한, call 메서드를 사용하여 함수에 인수를 직접 전달할 수 있습니다.

#### ⚙️ bind 메서드

bind 메서드는 함수와 this 값을 설정한 새로운 함수를 반환합니다. 원본 함수를 수정하지 않고 새로운 함수를 생성하며, bind로 생성한 함수는 항상 지정한 this 값을 가집니다. 이것은 이벤트 핸들러 함수 또는 콜백 함수에 유용하게 사용됩니다.

#### ⚙️ apply 메서드

apply 메서드는 함수를 호출하면서 this 값을 지정하고, 함수에 배열 형태의 인수를 전달할 수 있습니다. 첫 번째 인수는 this 값으로 설정하고, 두 번째 인수는 배열 형태로 함수에 전달됩니다.
