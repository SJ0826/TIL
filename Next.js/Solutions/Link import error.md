# Link import error

강의를 보며 코드를 따라 진행하던 중 Link가 정상적으로 import 되지 않았다.

```
import Link from 'next/head'

export async function getServerSideProps() {
  console.log('server');

  return {
    props: { time: new Date().toISOString() }
  }
}

export default function Home({ time }) {
  return (
    <>
      <h1 className="title">
        {time}
      </h1>
      <h1><Link href="/csr"><a>CSR 로</a></Link></h1>
      <h1><Link href="/csr"><a>SSG 로</a></Link></h1>
      <h1><Link href="/ISR"><a>ISR 로</a></Link></h1>
    </>

  )
}

```

## 원인

이유를 알기 위해 next.js 공식문서를 들어갔다.

**import 경로**가 잘못되었다.

근데 강의에선 `next/head`로 해도 잘 돌아갔다.

## 해결

`import Link from 'next/head'`를

`import Link from 'next/link'`로 고치면 해결된다.

## 출처

[Next.js 공식문서](https://nextjs.org/docs/api-reference/next/link)
