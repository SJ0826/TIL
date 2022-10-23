# Routing

### : 특정 주소에 도달해서 주소가 제공하는 데이터를 받아서 사용하는 과정

Next.js.의 Router는 file-system 기반이므로 파일을 만들면 즉각적으로 경로에 따라 라우팅된다.

## Next.js Routing 특징

- 리액트는 별도의 Router를 제공하지 않아서 `react-router-dom`이라는 라이브러리를 사용해야 하지만 , Next.js에서는 Router를 제공한다.

- `pages/index.js` 와 `src/index.js` 중에서 `pages/index.js`가 우선순위를 가진다.

- `jsconfig.json`에 절대경로를 설정할 수 있다.

```
// jsconfig.js 예시
...
{"compilerOption":{"baseUrl": "src"}}
...
```

- 원하는 폴더에 접근하고 싶으면 무조건 index.js파일을 만들어야한다.

## slug

### : 동적인 라우팅을 할 수 있는 방법

본래 slug는 중요한 의미를 포함하는 단어만을 이용해 제목을 작성하는 방법이다.

slug는 **대괄호**안에 넣은 값을 와일드 카드처럼 사용한다.

slug에 어떤 값을 넣어도 해당 파일로 이동한다.

파일뿐만 아니라 폴더에도 slug를 쓸 수 있다.

```
page/category/[slug].js => /category/:slug (ex. /category/food)
pages/[username]/info.js => /:username/info (ex. /jimmy/info)
```

`...`을 쓰면 무한 경로로 사용할 수 있다.

```
pages/cart/[...slug].js =? /cart/\* (ex. /cart/2022/06/24
```

한 동적 경로에는 한 개의 동적 페이지만 존재할 수 있다.

## 출처

- 패스트 캠퍼스 Next.js 완전 정복

* https://merrily-code.tistory.com/52
