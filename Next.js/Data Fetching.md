# Next.js가 제시하는 3 + 1 가지 Data Fetching 방법

*Next.js*는 서버사이드 렌더링을 효율적으로 할 수 있게 만들어주는 리액트 프레임워크이다.

Next.js에서 데이터를 fetching할 수 있는 여러가지 방법이 있다.

## 1. SSR(Server Side Render)

### : 서버에서 페이지를 구성하여 사용자에게 보여준다.

Next.js는 기본적으로 SSR을 지원한다.

처음부터 완성된 `HTML`을 받아서 렌더링한다.

- SSR을 담당하는 함수: `getServerSideProps`

```
export async function getServerSideProps() {
  console.log('server');
  return {
    props: { time: new Date().toISOString() }
  }
}

export default function Home({ time }) {
  ...
}
```

`getServerSideProps` 함수에서 `return`한 `props`가 `Home`에 적용된다.

`getServerSideProps` 함수는 server에서 데이터를 가져와서 `props`에 전달한다.

## CSR(Client Side Render)

### : 클라이언트가 데이터를 다운로드받아서 페이지를 완성한다.

유저가 작성된 코드를 다운로드하고 리액트가 렌더링하여 결과를 보여준다.

처음 서버에 데이터를 요청할때 빈 `HTML`을 받아온다.

CSR을 담당하는 함수는 없고 기존 리액트와 동일한 방식이다.

## SSG(Static-Site Generation)

### : 정적인 사이트를 만들기 위해 데이터를 가져와서 그려둔다.

build를 할때 정적페이지가 만들어진다. : build하는 타이밍에 데이터를 모두 가져와서 페이지를 생성한다.

개발환경(dev명령어를 통해 생성한 페이지)에서는 SSG가 SSR처럼 동작한다.

따라서 SSG를 보려면 build를 해야한다.

SSG는 블로그의 글을 보여주는것 처럼 Data Fetching을 적게할 때 많이 쓰여 서버 부하를 줄이고 효율성을 높일 수 있다.

- SSG를 담당하는 함수: `getStaticProps`

## ISR(Incremental Static Regeneration)

### : (특정 주기로) 정적인 사이트를 위해 데이터를 가져와서 다시 그려둔다.

증분 정적 사이트를 재생성한다

`revalidate`에 시간을 담당하는 값을 할당하여 데이터를 Fetching할 주기를 설정한다.

- 담당하는 함수: `getStaticProps` with revalidate

```
export async function getStaticProps() {
  console.log('server');

  return {
    props: { time: new Date().toISOString() },
    revalidate: 1, // 1초 리턴
  }
}
```

1초마다 다시 데이터를 fetching한다.

## 출처

- 패스트 캠퍼스 Next.js 완전 정복
- https://velog.io/@sji7532/Next-Next-js%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-SSR-CSR-%EA%B5%AC%ED%98%84
