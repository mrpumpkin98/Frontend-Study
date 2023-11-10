# 자료구조와 알고리즘\_배열

## ✅ 배열 생성 및 초기화

배열은 자바스크립트에서 중요한 데이터 구조다. 배열은 숫자, 문자열, 부울, 객체, 함수 등 모든 데이터 타입이 될 수 있는 값의 모음이다.

### 자바스크립트에서 배열 분해란?

자바스크립트의 배열 구조 분해를 사용하면 단일 문장으로 배열의 값을 개별 변수에 할당할 수 있다. ECMAScript6에 도입된 강력하고 간결한 기능이다.

**자바스크립트에서 배열 구조 분해 사용 방법**

```jsx
// 배열 생성
const colors = ["빨강", "파랑", "노랑"];

// 배열 구조 분해를 사용하여 각 요소를 변수에 할당
const [red, blue, yellow] = colors;

// 변수에 할당된 값 출력
console.log(red); // 출력: '빨강'
console.log(blue); // 출력: '파랑'
console.log(yellow); // 출력: '노랑'
```

### 자바스크립트에서 스프레드 연산자란?

자바스크립트에서 스프레드 연산자는 점(...) 3개로 표시된다. 이 연산자를 사용하면 배열의 내용을 새 배열이나 함수 인수로 확산할 수 있다. 여러 배열을 병합하거나 함수에 여러 인수를 전달해야 할 때 유용하다.

**스프레드 연산자 사용 방법**

**`배열 확장`**

```js
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const combinedArray = [...arr1, ...arr2];

console.log(combinedArray); // 출력: [1, 2, 3, 4, 5, 6]
```

**`배열 복제`**

```js
const originalArray = [1, 2, 3];
const copiedArray = [...originalArray];

console.log(copiedArray); // 출력: [1, 2, 3]
```

**`객체 확장`**

```js
const obj1 = { name: "Alice", age: 30 };
const obj2 = { job: "Engineer" };

const combinedObject = { ...obj1, ...obj2 };

console.log(combinedObject); // 출력: { name: 'Alice', age: 30, job: 'Engineer' }
```

**`객체 복제`**

```js
const originalObject = { a: 1, b: 2 };
const copiedObject = { ...originalObject };

console.log(copiedObject); // 출력: { a: 1, b: 2 }
```

## ✅ 배열 요소 액세스 및 수정하기

배열은 데이터 모음을 저장하고 저작할 수 있게 해주는 자바스크립트의 기본 데이터 구조다. 그렇다면 배열의 요소에 엑세스하려면 대괄호 표기법을 사용하여 액세스하려는 요소의 인덱스를 제공한다. 자바스크립트에서 배열 인덱스는 0 기반으로 fruits[1]을 사용하여 엑세스할 수 있다.

### 자바스크립트에서 나머지 매개변수란?

자바스크립트에서 "나머지 매개변수" 또는 "rest parameter"는 함수 정의에서 사용되는 매개변수 유형 중 하나다. 나머지 매개변수를 사용하면 함수가 임의의 수의 인수를 받아서 배열로 다룰 수 있다.

```js
function functionName(param1, param2, ...restParams) {
  // 함수 내부에서 restParams를 배열로 다룰 수 있음
}
```

```js
function sum(...numbers) {
  let result = 0;
  for (let number of numbers) {
    result += number;
  }
  return result;
}

console.log(sum(1, 2, 3, 4, 5)); // 출력: 15
```

### 자바스크립트 배열 메서드란?

자바스크립트에서 배열 메서드는 배열을 조작하고 데이터를 처리하기 위한 다양한 기능을 제공하는 메서드의 모음이다. 이러한 배열 메서드를 사용하면 배열의 요소를 추가, 제거, 변환 및 검색하는 등의 다양한 작업을 수행할 수 있다.

- **push() :** 배열의 끝에 하나 이상의 요소를 추가합니다.
- **pop() :** 배열의 끝에서 요소를 제거하고 반환합니다.
- **unshift() :** 배열의 시작에 하나 이상의 요소를 추가합니다.
- **shift() :** 배열의 시작에서 요소를 제거하고 반환합니다.

```jsx
const fruits = ["사과", "바나나", "딸기"];

fruits.push("오렌지"); // 배열 끝에 '오렌지' 추가
console.log(fruits); // 출력: ['사과', '바나나', '딸기', '오렌지']

const removedFruit = fruits.pop(); // 배열 끝의 요소 '오렌지'를 제거하고 반환
console.log(removedFruit); // 출력: '오렌지'

fruits.unshift("수박"); // 배열 시작에 '수박' 추가
console.log(fruits); // 출력: ['수박', '사과', '바나나', '딸기']

const shiftedFruit = fruits.shift(); // 배열 시작의 요소 '수박'을 제거하고 반환
console.log(shiftedFruit); // 출력: '수박'
```

- **concat() :** 두 개 이상의 배열을 결합하여 새로운 배열을 생성합니다.

```jsx
const numbers1 = [1, 2, 3];
const numbers2 = [4, 5, 6];

const combinedNumbers = numbers1.concat(numbers2); // 두 배열을 결합하여 새로운 배열 생성
console.log(combinedNumbers); // 출력: [1, 2, 3, 4, 5, 6]
```

- **map() :** 배열의 모든 요소에 대해 새로운 배열을 생성합니다.
- **filter() :** 주어진 조건에 따라 배열을 필터링하여 새로운 배열을 생성합니다.
- **reduce() :** 배열의 모든 요소를 순회하면서 값을 축소하거나 누적합니다.

```jsx
const numbers = [1, 2, 3, 4, 5];

const squaredNumbers = numbers.map(function (number) {
  return number * number;
});
console.log(squaredNumbers); // 출력: [1, 4, 9, 16, 25]

const evenNumbers = numbers.filter(function (number) {
  return number % 2 === 0;
});
console.log(evenNumbers); // 출력: [2, 4]

const sum = numbers.reduce(function (accumulator, number) {
  return accumulator + number;
}, 0);
console.log(sum); // 출력: 15
```

- **join() :** 배열의 모든 요소를 문자열로 결합하여 반환합니다.

```jsx
const fruits = ["사과", "바나나", "딸기"];
const fruitString = fruits.join(", "); // 배열 요소를 문자열로 결합 (구분자: ', ')
console.log(fruitString); // 출력: '사과, 바나나, 딸기'
```

- **slice() :** 배열의 일부분을 복사한 새로운 배열을 반환합니다.

```jsx
const colors = ["빨강", "파랑", "초록", "노랑", "주황"];
const selectedColors = colors.slice(1, 4); // 인덱스 1부터 4 이전까지의 요소를 복사
console.log(selectedColors); // 출력: ['파랑', '초록', '노랑']
```

- **splice() :** 배열의 요소를 추가, 제거 또는 교체합니다.

```jsx
const animals = ["사자", "호랑이", "곰", "원숭이"];
animals.splice(1, 2, "기린", "코알라"); // 인덱스 1부터 2개의 요소를 제거하고 '기린'과 '코알라'를 삽입
console.log(animals); // 출력: ['사자', '기린', '코알라', '원숭이']
```

- **forEach() :** 배열의 모든 요소에 대해 반복적으로 함수를 실행합니다.

```jsx
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(function (number) {
  console.log(number); // 배열의 각 요소에 대해 함수를 실행
});
// 출력:
// 1
// 2
// 3
// 4
// 5
```

- **find() :** 주어진 조건을 만족하는 첫 번째 요소를 반환합니다.
- **findIndex() :** 주어진 조건을 만족하는 첫 번째 요소의 인덱스를 반환합니다.

```jsx
const people = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 35 },
];

const charlie = people.find(function (person) {
  return person.name === "Charlie"; // 조건에 맞는 첫 번째 요소 반환
});

console.log(charlie); // 출력: { name: 'Charlie', age: 35 }

const bobIndex = people.findIndex(function (person) {
  return person.name === "Bob"; // 조건에 맞는 첫 번째 요소의 인덱스 반환
});

console.log(bobIndex); // 출력: 1
```

- **sort() :** 배열을 정렬합니다.
- **reverse() :** 배열의 요소 순서를 뒤집습니다.

```jsx
const numbers = [4, 2, 8, 5, 1];

numbers.sort(); // 배열을 정렬
console.log(numbers); // 출력: [1, 2, 4, 5, 8]

numbers.reverse(); // 배열의 요소 순서를 뒤집음
console.log(numbers); // 출력: [8, 5, 4, 2, 1]
```

## ✅ 일반적인 배열 연산

### 배열 정렬하기

- **sort() :** 메서드를 사용하여 배열을 정렬하는 코드를 제공한다.

```jsx
const fruits = ["사과", "바나나", "딸기", "오렌지"];

fruits.sort(); // 배열을 기본적으로 사전식으로 정렬

console.log(fruits); // 출력: ['딸기', '바나나', '사과', '오렌지']
```

### 배열 검색하기

- **indexOf() :** 메서드는 배열에서 지정된 요소의 첫 번째 인덱스를 찾아 반환한다. 만약 배열에서 해당 요소를 찾지 못하면 -1을 반환한다.

```jsx
const fruits = ["사과", "바나나", "딸기", "오렌지"];

const indexOfBanana = fruits.indexOf("바나나");
console.log(indexOfBanana); // 출력: 1 (인덱스 1에 '바나나'가 있음)

const indexOfMango = fruits.indexOf("망고");
console.log(indexOfMango); // 출력: -1 (배열에 '망고'가 없음)
```

### 배열 필터링하기

- **filter() :** 메서드는 주어진 함수의 조건을 만족하는 배열의 모든 요소를 추출하여 새로운 배열을 생성한다.

```jsx
const words = ["apple", "banana", "orange", "grape", "kiwi"];

// 길이가 5 이상인 단어들을 필터링하여 새로운 배열 생성
const longWords = words.filter(function (word) {
  return word.length >= 5;
});

console.log(longWords); // 출력: ['banana', 'orange']
```

- **reduce() :** 메서드는 배열의 각 요소에 대해 주어진 콜백 함수를 실행하고 하나의 최종 결과값을 반환한다.

```jsx
const words = ["Hello", " ", "world", "!"];

// 배열의 요소들을 문자열로 결합
const combinedString = words.reduce(function (accumulator, currentWord) {
  return accumulator + currentWord;
}, "");

console.log(combinedString); // 출력: 'Hello world!'
```

- **map() :** 메서드는 배열의 모든 요소에 대해 주어진 함수를 호출하고, 각 함수 호출의 결과를 모아서 새로운 배열을 생성한다.

```jsx
const numbers = [1, 2, 3, 4, 5];

// 각 숫자를 제곱하여 새로운 배열 생성
const squaredNumbers = numbers.map(function (number) {
  return number * number;
});

console.log(squaredNumbers); // 출력: [1, 4, 9, 16, 25]
```

## ✅ 다차원 배열

### 다차원 배열이란?

자바스크립트에서 다차원 배열은 다른 배열을 요소로 포함하는 배열이다. 행과 열이 있는 행렬이나 테이블로 생각할 수 있다. 이러한 배열은 일반적으로 여러 속성 또는 차원을 가진 데이터를 저장하고 조작하는 데 사용된다.

```jsx
// 2차원 배열 생성
const matrix2D = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];
```

```jsx
// 3차원 배열 생성
const matrix3D = [
  [
    [1, 2, 3],
    [4, 5, 6],
  ],
  [
    [7, 8, 9],
    [10, 11, 12],
  ],
];
```

### 다차원 바열의 요소에 엑세스하려면?

**2차원 배열 요소에 접근**

```jsx
// 2차원 배열 생성
const matrix2D = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

// 특정 위치의 요소에 접근
const elementAtRow2Col1 = matrix2D[1][0];
console.log(elementAtRow2Col1); // 출력: 4
```

**3차원 배열 요소에 접근**

```jsx
// 3차원 배열 생성
const matrix3D = [
  [
    [1, 2, 3],
    [4, 5, 6],
  ],
  [
    [7, 8, 9],
    [10, 11, 12],
  ],
];

// 특정 위치의 요소에 접근
const elementAtLayer2Row1Col2 = matrix3D[1][0][1];
console.log(elementAtLayer2Row1Col2); // 출력: 8
```

## ✅ 배열 연산의 시간 및 공간 복잡도 분석

**Push (배열의 끝에 요소 추가)**
</br>
시간 복잡도: O(1) - 상수 시간이 소요됩니다.
</br>
공간 복잡도: O(1) - 추가된 요소 하나만큼의 공간이 필요합니다.

**Pop (배열의 끝에서 요소 제거)**
</br>
시간 복잡도: O(1) - 상수 시간이 소요됩니다.
</br>
공간 복잡도: O(1) - 제거된 요소 하나만큼의 공간이 반환됩니다.

**Shift (배열의 시작에서 요소 제거)**
시간 복잡도: O(n) - 배열의 모든 요소를 이동해야 합니다.
공간 복잡도: O(1) - 제거된 요소 하나만큼의 공간이 반환됩니다.

**Unshift (배열의 시작에 요소 추가)**
</br>
시간 복잡도: O(n) - 배열의 모든 요소를 이동해야 합니다.
</br>
공간 복잡도: O(1) - 추가된 요소 하나만큼의 공간이 필요합니다.

**Splice (배열의 요소 추가, 제거 또는 교체)**
</br>
시간 복잡도: O(n) - 추가, 제거 또는 교체되는 요소들 이후의 모든 요소를 이동해야 합니다.
</br>
공간 복잡도: O(1) - 추가된 요소나 제거된 요소의 개수에 따라 변할 수 있습니다.

**Slice (배열의 일부분을 복사)**
</br>
시간 복잡도: O(k) - 복사할 요소의 개수에 비례합니다 (k는 복사하는 요소의 개수).
</br>
공간 복잡도: O(k) - 복사된 요소들을 저장할 새로운 배열이 필요합니다.
