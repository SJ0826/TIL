# Sass (Syntactically Awesome Style Sheets)

### : CSS가 만들어지기 전에 이런저런 일들을 먼저 처리해주는 전처리기(Preprocessor) 언어 (like JS & Ts)

### Sass를 사용하는 이유

- 보다 간편한 CSS구조화
- 높은 가독성과 재사용성
- 추가 도구 제공
  - 변수 사용가능: CSS 속성값을 통일해서 관리가능
  - 조건문과 반복문
  - Import (모듈화)
  - Nesting (선택자 반복 작성을 줄여주는 기능)
  - Mixin (함수 개념)
  - Extend/Inheritance (확장/상속)

### Sass 시작하기

#### 0. node.js 설치

#### 1. 설치하기

`npm install sass -g`

#### 2. 설치 확인

`npm show sass version`

#### 3. Sass 실행

`node-sass [옵션] <인풋파일> <아웃풋파일>`
`node-sass -w scss/style.scss css/style.css --output-style compressed`

#### 4. Sass watch 옵션 사용하기: 자동으로 변경 사항을 컴파일

`node-sass --watch styles/common.scss styles/common.css`

#### 5. VS Code 익스텐션 설치

- Live Sass Compiler
- scss-lint - Visual Studio Marketplace
- SCSS Formatter - Visual Studio Marketplace
- scss snippet - Visual Studio Marketplace
- SCSS Scope Helper - Visual Studio Marketplace

여기까지 진행해서 `.scss` 파일 생성시 vscode하단에 `scss-watching` 표시가 뜬다.
클릭시 자동으로 수정사항을 감지해 컴파일을 진행한다.

#### 6. SCSS / CSS 폴더 분리

scss는 서버가 인식하지 못하기 때문에 필요가 없다.
따라서 서버에 올라가지 않도록 설정해주어야 한다.

```
// setting.json

{
    "liveSassCompile.settings.generateMap": false, // 만일 .map 파일 생성을 끄고 싶다면
    "liveSassCompile.settings.formats": [
    {
        "format": "expanded",
        "extensionName": ".css",
        "savePath": 경로 // ex. "~/../css"
    }
    ],
    "liveServer.settings.donotShowInfoMsg": true
}
```

## 출처

- [Dev Scroll-SCSS](https://inpa.tistory.com/entry/SCSS-%F0%9F%92%8E-SassSCSS-%EB%9E%80-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%BB%B4%ED%8C%8C%EC%9D%BC)
