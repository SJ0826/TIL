# Link 태그와 a 태그의 차이

```
<a href=”/posts/first-post”>a 태그 사용</a>
<Link href=”/posts/first-post”><a>Link 태그 사용</a></Link>
```

## 차이점 1. Client Side Navigate

a 태그를 사용하는 것은 브라우저 주소 창에 새로운 주소를 입력한 것과 같다.

Link태그의 최적화 도구들이 사용되지 않는다.

Link태그를 이용하면 페이지에서 필요한 데이터만 추가적으로 가져온다.

html이 리로드되지 않는다.

특정 JS만 로드된다.

사용자에게 다르게 보여주어야 하는 부분만 추가적으로 가져와서 빠르게 동작하게 할 수 있는 최적화 기능이 탑재되어 있다.

이것을 **Client Side Navigate**라고 한다.

## 차이점 2. Prefetching(미리-fetching)

<Link> 컴포넌트를 이용하면, ViewPort(사용자 화면)에 Link 컴포넌트가 노출되었을 때만 `href`로 연결된 페이지의 부분(chunk)를 미리 로드한다.

따라서 해당 링크를 클릭했을땐 이미 데이터를 로드했기 때문에 JS에서 가져올 데이터가 없다.

이를 통해 성능을 최적화 한다.

## a 태그는 언제 사용할까?

- 본 서비스 외부 링크로 연결 할 때는 <a>태그를 쓴다.
- Link component에 스타일을 줄 때는 <a>태그에 주어야 한다.

## 출처

- 패스트 캠퍼스 Next.js 완전 정복
