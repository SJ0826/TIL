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

## Next.js Routing 방법

### 1. 정적 라우팅(Link)

#### : 사전에 지정된 주소로 이동하는 방법

`Link`컴포넌트를 사용해 주소를 이동한다.

<Link href = "해당경로">...</Link>

### 2. 동적라우팅(slug)

#### : 페이지가 상황에 따라 동적으로 경로가 지정된다.

본래 slug는 중요한 의미를 포함하는 단어만을 이용해 제목을 작성하는 방법이다.

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

#### slug 사용법

Next.js에서 제공하는 `useRouter`사용해서 Router의 `query`로 컨트롤한다.

```
import { useRouter } from 'next/router'
...
const router = useRouter()
const {slug} = router.query
...
```

만약 `query`에도 `slug`가 있다면 `page`에서 사용한 `slug`가 우선시된다.

slug는 file-system기반이기 때문이다.

#### 다중 slug

```
// pages/[username]/[info].js
...
import { useRouter } from 'next/router'
...
const router = useRouter()
const{ username, info } = router.query
```

`query`에서 `username`과 `info`가 각각 할당되어 페이지가 로드된다.

`/[...slug].js`는 배열로 받아진다.

#### 옵셔널 slug

slug 값이 없어도 동작하게 만드려면 `[[...slug]]`처럼 대괄호를 두번씩 사용하면 된다.

### 3. Shallow Routing

#### : `getServerSidePros` / `getStaticProps` 등을 다시 실행시키지 않으면서 현재 상태를 잃지 않고 url을 바꾸는 방법

Shallow의 뜻은 '얉은'이라는 뜻을 가지고 있다.

Shllow Routing을 사용하는 경우는 상태를 유지하면서 url을 바꾸고 싶을 때 이다.

예를 들어 사용자가 어떤 동작을 했고, 그 기록을 `query`로 남기고 싶을때, `query`로 남기면 사용자가 새로고침을 해도 유지된다.

#### url을 바꾸는 3가지 방법

1. `location.replace("url")`: 로컬 `state`는 유지 안됨(리렌더)
2. `router.push(url)`: 로컬 `state`는 유지 / data fetching은 일어남
3. `router.push(url, as, {shallow: true })`: 로컬 `state` 유지 / data fetching은 일어나지 않음

## 출처

- 패스트 캠퍼스 Next.js 완전 정복

* https://merrily-code.tistory.com/52
