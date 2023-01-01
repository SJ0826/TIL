# React.lazy
**React.lazy**는 React에서 동적으로 컴포넌트 파일을 불러올 때 사용합니다.

규모가 큰 프로젝트의 경우 한 페이지에 수많은 컴포넌트를 `import`합니다.

정적으로 컴포넌트를 `import`한다면 첫 페이지를 로드하는 즉시 대규모 단일 Javascript번들이 사용자에게 전송됩니다.

따라서 동적으로 `import`하여 필요할때만 컴포넌트를 로드하는 작업이 필요합니다.

### 사용법
#### [React.lazy()]
```js
const Home = lazy(() => import('./routes/Home'));
const About = lazy(() => import('./routes/About'));
```
* 불러오는 파일은 React 컴포넌트를 포함해야 합니다.
* `default export`를 가진 컴포넌트여야 합니다.

#### [Suspense]
```js
const App = () => (
  <Router>
    <Suspense fallback={<div>Loading...</div>}>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Suspense>
  </Router>
);
```
* `fallback`: 컴포넌트가 로드될 때까지 기다리는 동안 보여줄 React 엘리먼트입니다.
* 하나의 `Suspense` 컴포넌트가 여러개의 `lazy`컴포넌트를 감쌀 수 있습니다.

## 출처
* [리액트 공식문서 - 코드 분할](https://ko.reactjs.org/docs/code-splitting.html)