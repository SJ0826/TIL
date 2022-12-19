# CNA 없이 프로젝트 셋팅하기

next.js + typescript를 사용할 때 CNA없이 프로젝트를 생성하는 나만의 방법 정리.

사용 패키지 매니저 : `yarn` 또는 `npm`

## 1. npm 설정

```
npm init -y
```

해당 명령어를 실행하면 nodejs의 모듈 관리를 위해 사용되는 `package.json`파일이 생성된다.
패키지에 관한 정보와 사용하는 라이브러리 등의 정보를 알 수 있다.
`-y`옵션은 yes의 의미로 가장 기본적인 값으로 셋팅을 하겠다는 의미이다.

## 2. Next & TS 설치

```
// next 설치
yarn add react next react-dom
yarn add --dev typescript @types/react @types/node eslint eslint-config-next
```

위의 명령어를 입력하고 `package.json`에 "script"에 관한 내용을 입력한다.

```
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start",
  "lint": "next lint"
}
```

- `dev`: development mode
- `build`: production mode를 위한 application의 빌드
- `start`: producttion server의 시작

## 3. ESLint 설치

```
npm i -D eslint eslint-config-airbnb-base babel-eslint eslint-config-prettier
```

ESLint는 자바스크립트 문법 중 문제가 있는 곳에 `error`나 `warning`표시를 해서 보여주어 일관성 있는 코드작성을 도와준다.

많은 스타일 가이드가 있지만 많은 개발자들이 사용하는 **Airbnb Style Guide**를 사용하겠다.

```
npx eslint --init
```

이 명령어는 eslint를 초기화 해주어 환경설정 파일인 `.eslintrc`를 생성해준다.
`.eslintrc`에서는 사용자에 맞게 rule을 설정해서 사용할 수 있다.

```
// .eslintrc.json
{
  "env": {
    "browser": true,
    "es2021": true,
    "jest": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "airbnb-base",
    "prettier"
  ],
  "overrides": [],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "plugins": ["react", "@typescript-eslint"],
  "rules": {
    "no-console": "warn",
    "no-plusplus": "off",
    "no-shadow": "off",
    "vars-on-top": "off",
    "no-underscore-dangle": "off", // var _foo;
    "func-names": "off", // setTimeout(function () {}, 0);
    "prefer-arrow-callback": "error", // Require using arrow functions for callbacks
    "prefer-template": "off",
    "no-nested-ternary": "off",
    "max-classes-per-file": "off",
    "wrap-iife": ["error", "inside"],
    "arrow-parens": "off", // a => {}
    "no-restricted-syntax": [0, "ForOfStatement"], // disallow specified syntax(ex. WithStatement)
    "no-param-reassign": ["error", { "props": false }],
    "require-await": "error",
    "import/no-extraneous-dependencies": ["error", { "devDependencies": true }],
    "react/react-in-jsx-scope": "off",
    "no-use-before-define": "off",
    "import/no-unresolved": "off",
    "import/extensions": "off",
    "class-methods-use-this": "off",
    "arrow-body-style":"off",
    "no-unused-expressions":"off",
    "no-unused-vars":"off",
    "import/prefer-default-export": "off",
    "no-useless-catch": "off",
    "no-alert": "off"
  }
}
```

### eslint가 잘 적용되고 있는 지 검사하는 방법

1. `npx eslint 검사하고_싶은_파일명.js`
2. `npx eslint 검사하고_싶은_파일명.js --fix`
3. extension에서 eslint설치 후 `settings.json`에서 설정 추가

```
  "editor.codeActionsOnSave": {
        "source.fixAll": true,
    },
    "editor.formatOnSave": true,

```

4. Prettier 설치

```
yarn add -D prettier
```

Prettier는 vscode의 code formater이다.
명령어를 실행하면 package.json에 prettier가 추가된 것을 확인할 수 있다.
`.prettierrc`에서 코드 작성 규칙을 사용자에 맞게 설정할 수 있다.

```
// .prettierrc
{
  "singleQuote": true,
  "parser": "typescript",
  "semi": false,
  "useTabs": false,
  "tabWidth": 2,
  "printWidth": 120,
  "jsxSingleQuote": false,
  "trailingComma": "all"
}
```

## 5. tsconfig 파일 추가

`tsconfig`는 타입스크립트 설정 파일이다.
타입스크립트를 자바스크립트로 변환할 때 쓰이는 설정을 정의해놓았다.

```
// tsconfig.json

{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
     "baseUrl": ".",
    "paths": {
      "@ui/*": ["ui/*"],
      "@components/*": ["ui/components/*"],
    },
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true
  },
  "include": [
    "next-env.d.ts", "**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules"]
}
```

## 6. .gitignore

.gitignore은 원하지 않는 파일이 깃에 커밋되지 않게 막아준다.

```
// .gitignore

# See https://help.github.com/articles/ignoring-files/ for more about ignoring files.

# dependencies
/node_modules
/.pnp
.pnp.js

# testing
/coverage

# next.js
/.next/
/out/

# production
/build

# misc
.DS_Store
*.pem

# debug
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.pnpm-debug.log*

# local env files
.env*.local

# vercel
.vercel

# typescript
*.tsbuildinfo

.idea
```

## 7. pages 폴더 설정

dev를 돌렸을 때 보여지는 pages를 위한 설정

```
// pages/_app.tsx

import type { AppProps } from 'next/app';
import Head from 'next/head';

import GlobalStyles from '../ui/core/GlobalStyles';

function MyApp({ Component, pageProps }: AppProps) {
  return (
    <>
      <Head>
        <title>타이틀이 보여집니다.</title>
      </Head>
      <GlobalStyles />
      <Component {...pageProps} />
    </>
  );
}

export default MyApp;
```

```
// pages/_document.tsx

import Document, {
  DocumentContext,
  Head,
  Html,
  Main,
  NextScript,
} from 'next/document';
import { ServerStyleSheet } from 'styled-components';

class AppDocument extends Document {
  static async getInitialProps(context: DocumentContext) {
    const sheet = new ServerStyleSheet();
    const originalRenderPage = context.renderPage;
    context.renderPage = () => originalRenderPage({
      enhanceApp: (App) => (props) => sheet.collectStyles(<App {...props} />),
    });
    const initialProps = await Document.getInitialProps(context);
    return {
      ...initialProps,
      styles: (
        <>
          {initialProps.styles}
          {sheet.getStyleElement()}
        </>
      ),
    };
  }

  render() {
    return (
      <Html>
        <Head />
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}

export default AppDocument;
```

```
// pages/index.tsx

import React from 'react';
import type { NextPage } from 'next';
import styled from 'styled-components';

const Home: NextPage = () => (
  <Container>
    테스트화면 입니다.
  </Container>
);

export default Home;

const Container = styled.div`
  background-color: #5a8fcd;
`;
```

```
// ui/compoments/core/GlobalStyles.ts

import { createGlobalStyle } from 'styled-components'

const GlobalStyles = createGlobalStyle`
  html {
    height: 100%;
  }
  body {
    height: auto;
    margin: 0;
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    overflow-x: hidden;
    touch-action: none;
  }
  *,
  *:before,
  *:after {
    box-sizing: inherit;
  }
  a {
    text-decoration: none;
    color: inherit;
  }
`

export default GlobalStyles

```

## 출처

[ESLint설치하기, 설정방법](https://lakelouise.tistory.com/199)
[타입스크립트 핸드북](https://joshua1988.github.io/ts/config/tsconfig.html#%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%84%A4%EC%A0%95-%ED%8C%8C%EC%9D%BC-%EC%9D%B8%EC%8B%9D-%EA%B8%B0%EC%A4%80)
