# 모듈 번들러

## 모듈(Module)이란?!

[[프론트엔드 전반] 모듈 시스템](https://velog.io/@sju4486/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EC%A0%84%EB%B0%98-%EB%AA%A8%EB%93%88-%EC%8B%9C%EC%8A%A4%ED%85%9C)

모듈은 파일 하나하나, 특정 기능을 갖는 작은 코드 단위를 의미한다. 우리가 개발을 하면서 규모가 커지면 언젠가 파일을 여러 개로 분리해야 하는 시점이 온다. 이때 분리된 파일 각각을 모듈이라고 부르는 것이다. 목적에 따라, **기능별로 여러 개의 파일로 분리해서 관리할 수 있으며 모듈로 분리하는 과정**을 **`모듈화`** 라고 한다.

## 모듈 번들러(Module bundler)

> ![](https://velog.velcdn.com/images/sju4486/post/e877b8d2-37da-44e3-8359-892838a62e1e/image.png)

웹 애플리케이션을 구성하는 몇십, 몇백 개의 자원들을 하나로 병합 및 압축해주는 동작을 모듈 번들링이라하며 번들링을 할 수 있게 합쳐주는 도구가 번들러이다. 즉, **`모듈 번들러`** 는 **여러 개의 파일을 하나의 파일로 합쳐주는 역할**을 한다.

> 💡 **모듈 번들러가 필요한 이유**
>
> 모듈을 이용하는 것은 좋지만 모든 파일을 네트워크 통신을 통해 가져와야 한다. **파일 하나하나 요청하고 가져온다면 로딩 속도는 늦어질 것이다.** 또한 웹 서비스를 개발하고, 배포할 때 HTML, CSS, JS압축, 이미지 압축, CSS 전처리기 변환과 같은 작업들을 해야 했다. **그래서 로딩 속도 개선과 이러한 일들을 자동화해주는 도구들이 필요**했고, Grunt와 Gulp 같은 도구들이 등장했다.

## 웹팩 (Webpack)

웹팩(Webpack)은 **웹 애플리케이션을 개발할 때 사용하는 모듈 번들러**다. 모듈 번들러는 웹 애플리케이션의 자원들을 하나로 묶어주고, 이를 최적화하여 **더 효율적으로 웹 페이지를 제공할 수 있도록 도와준다.**

- **`모듈 번들링`** : 웹팩은 JavaScript 파일뿐만 아니라 HTML, CSS, 이미지 등의 다양한 자원을 모듈로 간주하고 이를 번들링한다. 이렇게 **번들링된 자원들은 브라우저에서 요청 시 각각 따로 가져오는 것보다 더 빠르게 로드**된다.

- **`엔트리 포인트(Entry Point)`** : 웹팩은 애플리케이션의 시작점을 지정하는데, 이를 엔트리 포인트라고 한다. 보통 하나 이상의 엔트리 포인트가 있고, **각 엔트리 포인트에서부터 의존하는 모듈을 추적**하여 번들링한다.

- **`로더(Loader)`** : 웹팩은 **JavaScript 이외의 자원을 번들링하기 위해 로더를 사용**한다. 로더는 파일을 읽고 변환하는 역할을 한다. 예를 들어, CSS 파일을 JavaScript로 변환하여 번들에 포함시키는 로더를 사용할 수 있다.

- **`플러그인(Plugin)`** : 웹팩의 **기능을 확장하고 최적화하기 위해 플러그인을 사용**한다. 예를 들어, **코드 압축, 번들 최적화, 환경 변수 주입** 등 다양한 작업을 수행하는 플러그인을 추가할 수 있다.

- **`번들(Bundle)`**: 번들은 웹팩에서 생성된 최종 결과물을 의미한다. 이것은 하나 이상의 JavaScript 파일과 해당 자원들을 포함하며, 브라우저에서 로드하여 애플리케이션을 실행하는 데 사용된다.

## React 개발환경 직접 구성하기 (babel + webpack)

지금까지 새로운 리액트 프로젝트 개발을 시작할 때 **create-react-app**을 사용해왔다. create-react-app은 리액트 개발에 필요한 **웹팩, 바벨, 테스트 라이브러리** 등 다양한 환경을 한 번에 제공해준다. 그러나 내 프로젝트에 맞춤인 개발환경을 구축하고 싶다면 리액트 개발환경을 직접 구성해보는 시도를 해보는 것이 좋다.

### 1. 프로젝트 초기화

```jsx
npm init -y
```

### 2. 폴더구조 생성

```
My Project
│
└─public
│   └─ index.html
└─src
│   └─ index.js
└─package.json
```

`index.html을 생성`

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>MyProject</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```

### 3. Babel

```
npm install --save-dev @babel/core @babel/cli @babel/preset-env @babel/preset-react
```

` .babelrc라는 바벨 설정 파일 생성`

```jsx
{
  "presets": ["@babel/env", "@babel/preset-react"]
}
```

### 4. Webpack

- webpack-cli는 CLI(Command Line Interface)에서 웹팩을 사용하기 위한 패키지
- webpack-dev-server는 코드를 수정하면 자동으로 메모리상에 재빌드를 해주기 때문에 빠르고 편리한 개발을 도와주는 패키지

```
npm install --save-dev webpack webpack-cli webpack-dev-server
```

- 웹팩 설정에 필요한 로더, 플러그인 패키지들을 설치

```
npm install --save-dev html-webpack-plugin css-loader style-loader file-loader babel-loader
```

`webpack.config.js 생성`

```jsx
const path = require("path");
const webpack = require("webpack");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  entry: path.join(__dirname, "src", "index.js"),
  mode: "development",
  output: {
    path: path.resolve(__dirname, "dist"),
  },
  module: {
    rules: [
      {
        test: /\.?(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader",
          options: {
            presets: ["@babel/preset-env", "@babel/preset-react"],
          },
        },
        resolve: {
          extensions: ["", ".js", ".jsx"],
        },
      },
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.(png|jp(e*)g|svg|gif)$/,
        use: ["file-loader"],
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.join(__dirname, "public", "index.html"),
    }),
    new webpack.HotModuleReplacementPlugin(),
  ],
  devServer: {
    hot: true,
    host: "localhost",
    port: 3001,
  },
};
```

`package.json에 가서 웹팩 개발 서버 실행 명령을 등록`

```jsx
"scripts": {
   "test": "echo \"Error: no test specified\" && exit 1",
   "start": "webpack-dev-server --mode development"
 },
```

### 5. React

```
npm install react react-dom
```

### 6. 최종 확인

```
My Project
│
└─public
│   └─ index.html
└─src
│   └─ index.js
│   └─ App.css
│   └─ App.jsx
└─.babelrc
└─webpack.config.js
└─package.json
```

` App.css`

```css
h1 {
  color: blue;
}
```

`App.jsx`

```jsx
import React from "react";
import "./App.css";

class App extends React.Component {
  render() {
    return (
      <div className="App">
        <h1> Hello, World!? </h1>
      </div>
    );
  }
}

export default App;
```

`index.js`

```jsx
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById("root")
);
```

- npm run start 명령을 실행한

```
npm run start
```

## 참고

- https://bribrie.tistory.com/84
- https://webpack.kr/concepts/#entry
