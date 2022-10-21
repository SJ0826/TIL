Data Fetching = 데이터 가져오기

Next.js가 제시하는 3 + 1 가지 Data Fetching 방법
-SSR
Server sSide Render
서버가 그린다.
서버가 데이터를 가져와서 그린다.
SSR을 담당하는 함수: getServerSideProps

```
export async function getServerSideProps() {
  console.log('server');
  return {
    props: { time: new Date().toISOString() }
  }
}
```

- getServerSideProps 함수에서 return한 props가 Home에 적용된다.
- getServerSideProps 함수는 server에서 데이터를 가져와서 props에 전달한다.

-CSR
Client Side Render
클라이언트가 그린다.: 클라이언트가 데이터를 가져와서 그린다.
CSR을 담당하는 함수는 없음. 기존 리액트와 동일

-SSG
Static-Site Generation
정적인 사이트 생성: 정적인 사이트를 데이터를 가져와서 그려둔다.
SSG를 담당하는 함수: getStaticProps
주의
개발환경(dev명령어를 통해 생성한 페이지)에서는 SSG가 SSR처럼 동작한다.
SSG를 보려면 build를 해야한다.

build를 할때 정적페이지가 만들어진다. : build하는 타이밍에 데이터를 모두 가져와서 페이지를 생성한다.

언제쓰여?
SSR: Data Fetching을 많이 할때
SSG: 정적인 페이지. Data Fetching을 적게할때 ex 블로그 글 -> 서버 부하를 줄이고 효율성을 높인다.
