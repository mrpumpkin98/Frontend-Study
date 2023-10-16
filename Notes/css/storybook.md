# Storybook

## Storybook이란?

storybook은 **UI 컴포넌트를 모아서 보여주고 문서화하는 오픈소스 툴**이다.
즉 React, Angular, Vue 등의 **분리된 UI 컴포넌트를 체계적이고 효율적으로 구축할 수 있는 개발 도구**이다.

**스토리북(Storybook)** 을 기본 구성 단위는 **스토리(Story)** 이며 하나의 UI 컴포넌트는 보통 하나 이상의 Story를 가지게 된다. 각 Story는 해당 UI 컴포넌트가 어떻게 사용될 수 있는지를 보여주는 하나의 예다.

Storybook을 사용하면 UI 컴포넌트가 각각 독립적으로 **어떻게 실제로 랜더링되는지 직접 시각적으로 테스트하면서 개발을 진행할 수 있다.**

## Storybook 설치

```tsx
$ npx @storybook/cli sb init
```

```tsx
$ yarn add --dev react-docgen-typescript-loader
```

- story북 실행했을 때 컴포넌트 테이블 만들기 위해 설치

![](https://velog.velcdn.com/images/sju4486/post/74a7eb24-6d81-4635-a9a7-f03fa5d97e16/image.png)

## Storybook 설정

`.storybook/config.js` 파일을 열고, src 디렉터리 내부에 `stories.js`로 끝나는 모든 파일이 Story로 인식되도록 설정해준다.

```tsx
import { configure } from "@storybook/react";

// automatically import all files ending in *.stories.js
// configure(require.context('../src/stories', true, /\.stories\.js$/), module);
configure(require.context("../src", true, /\.stories\.js$/), module);
```

## React 컴포넌트 작성

- `src/components` 디렉터리를 생성하고, 그 안에 Text.jsx 파일을 생성하고, 그 파일 안에 아래 코드를 작성한다.
- UI 컴포넌트 props로 넘어온 `color`, `italic`, `underline`에 따라서 다른 스타일이 적용된 children prop을 랜더링해준다.

```tsx
import React from "react";
import PropTypes from "prop-types";

export function Text({ children, color, italic, underline }) {
  const style = {
    color: color,
    fontStyle: italic ? "italic" : "normal",
    textDecoration: underline ? "underline" : "none",
  };
  return <span style={style}>{children}</span>;
}

Text.propTypes = {
  children: PropTypes.string.isRequired,
  color: PropTypes.string,
  italic: PropTypes.bool,
  underline: PropTypes.bool,
};

Text.defaultProps = {
  color: "black",
  italic: false,
  underline: false,
};
```

|    프로퍼티    | 설명                                                                                                                                                                                    |
| :------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|     title      | Storybook의 사이드바에 표시될 스토리 이름. /로 구분할 경우 그룹과 스토리 이름을 구분할 수 있다. 예를 들어, 위 예제의 title: 'Example/Button'은 Example 그룹의 Button 스토리로 표시된다. |
|   component    | 컴포넌트                                                                                                                                                                                |
|      args      | 모든 스토리에 공통으로 전달될 props. 예를 들어, 위 예제의 backgroundColor: '#000'는 모든 스토리 공통으로 컴포넌트에게 backgroundColor props를 전달한다.                                 |
|    argTypes    | 각 Story args의 행동(behaviour) 방식 설정. 예를 들어, 위 예제의 backgroundColor: { control: 'color' }은 controls에서 선택한 컬러를 컴포넌트의 props로 전달하겠다는 의미다.              |
|   decorators   | Story를 래핑하는 추가 렌더링 기능                                                                                                                                                       |
|   parameters   | Story에 대한 정적 메타 데이터 정의                                                                                                                                                      |
| excludeStories | 렌더링 제외 설정                                                                                                                                                                        |

## Story 추가

- `src/components` 디렉터리를 안에 `Text.stories.ts` 파일을 생성하고, 그 파일 안에 아래 코드를 작성한다.
- default 임포트는 해당 UI 컴포넌트에 대한 메타 정보를 객체로 작성하는데 title은 Storybook 메뉴에서에서 해당 컴포넌트가 뭐라고 표시될지를 결정하고, component에는 위에서 작성한 React 컴포넌트를 지정한다.
- 그 다음 4개의 named 임포트에는 UI 컴포넌트의 활용 예시를 나타내는 Story를 하나씩 함수 형태로 작성한다.

```tsx
import React from "react";
import { Text } from "./Text";

export default {
  title: "Text",
  component: Text,
};

const STORY_TEXT = "I love Storybook!";

export const Default = () => <Text>{STORY_TEXT}</Text>;

export const Red = () => <Text color="red">{STORY_TEXT}</Text>;

export const Italic = () => <Text italic>{STORY_TEXT}</Text>;

export const Underline = () => <Text underline>{STORY_TEXT}</Text>;
```

## StoryBook 구동

```tsx
$ npm run storybook
```

## 참고

- https://storybook.js.org/docs/react/get-started/install
- https://blog.haeyum.me/web/Storybook
- https://www.daleseo.com/storybook
