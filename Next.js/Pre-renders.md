# Pre-renders

### : 서버측에서 페이지를 미리 만들어 놓는다.

서버에서 페이지를 미리 만들기 때문에 클라이언트에서 페이지를 로드할 때 이미 많은 부분이 그려져있다.

이후에 JS가 로드되면 Hydration라는 과정을 거쳐 사용자와 앱이 인터렉션한다.

## Pre-rendering과 SEO의 상관관계

CSR만 제공한다면 Client(브라우저)처럼 동작하지 않는 검색엔진의 경우 처음에 빈 HTML화면만 로드되기 때문에 아무런 데이터도 조회할 수 없다.

Pre-render를 해두면 Client처럼 동작하지 않는 검색엔진에게 필요한 데이터를 제공할 수 있다.

## Next.js의 두가지 Pre-rendering방식

### 1. SSG

- SSG는 빌드 타임에 pre-render한다.
- 따라서 서버 부하가 적다.
- Next.js가 권장한다.

Page의 내용물이 외부 데이터에 의존적인 상황에는 `getStaticProps`만 가지고도 가능하지만

Page Paths까지 외부 데이터에 의존적인 상황에는 `getStaticPaths`도 함께 활용해야 가능하다.

## 2. SSR

- SSR은 요청 타임에 pre-render한다.
- 사용자가 페이지에 접근할때 pre-render하기 때문에 접근할때 마다 서버 부하가 발생한다.
