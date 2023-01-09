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
prettier에서 제공하는 옵션들은 다음과 같다.
```
{
  "arrowParens": "avoid", // 화살표 함수 괄호 사용 방식
  "bracketSpacing": false, // 객체 리터럴에서 괄호에 공백 삽입 여부 
  "endOfLine": "auto", // EoF 방식, OS별로 처리 방식이 다름 
  "htmlWhitespaceSensitivity": "css", // HTML 공백 감도 설정
  "jsxBracketSameLine": false, // JSX의 마지막 `>`를 다음 줄로 내릴지 여부 
  "jsxSingleQuote": false, // JSX에 singe 쿼테이션 사용 여부
  "printWidth": 80, //  줄 바꿈 할 폭 길이
  "proseWrap": "preserve", // markdown 텍스트의 줄바꿈 방식 (v1.8.2)
  "quoteProps": "as-needed" // 객체 속성에 쿼테이션 적용 방식
  "semi": true, // 세미콜론 사용 여부
  "singleQuote": true, // single 쿼테이션 사용 여부
  "tabWidth": 2, // 탭 너비 
  "trailingComma": "all", // 여러 줄을 사용할 때, 후행 콤마 사용 방식
  "useTabs": false, // 탭 사용 여부
  "vueIndentScriptAndStyle": true, // Vue 파일의 script와 style 태그의 들여쓰기 여부 (v1.19.0)
  "parser": '', // 사용할 parser를 지정, 자동으로 지정됨
  "filepath": '', // parser를 유추할 수 있는 파일을 지정
  "rangeStart": 0, // 포맷팅을 부분 적용할 파일의 시작 라인 지정
  "rangeEnd": Infinity, // 포맷팅 부분 적용할 파일의 끝 라인 지정,
  "requirePragma": false, // 파일 상단에 미리 정의된 주석을 작성하고 Pragma로 포맷팅 사용 여부 지정 (v1.8.0)
  "insertPragma": false, // 미리 정의된 @format marker의 사용 여부 (v1.8.0)
  "overrides": [ 
    {
      "files": "*.json",
      "options": {
        "printWidth": 200
      }
    }
  ], // 특정 파일별로 옵션을 다르게 지정함, ESLint 방식 사용
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
