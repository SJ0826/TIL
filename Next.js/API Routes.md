# API Routes

API Routes는 **Next.js에서 API를 구축하기 위한 방법**이다.

`pages/api`에 있는 어떤 파일이 `/api/*` 에 매핑되면

`page`대신 API 엔드포인트로서 다뤄질 것이다.

그 파일들은 server-side 번들이라 client-bundle의 크기를 증가시키지 않는다.

다음은 `json` response를 HTTP code `200`으로 반환하는 API Route 이다.

```
export default function handler(req, res) {
  res.status(200).json({ name: 'John Doe' })
}
```

API Route가 실행되기 위해서 핸들러 함수를 export해야 한다.

서로 다른 HTTP method들을 다루기 위해서, 핸들러 함수 안에 `req.method`를 사용해야 하면된다.

```
export default function handler(req, res) {
  if (req.method === 'POST') {
    // Process a POST request
  } else {
    // Handle any other HTTP method
  }
}
```

## Dynamic API Routes

API Routes는 동적 라우팅을 지원한다.

```
// pages/api/post/[pid].js

export default function handler(req, res) {
  const { pid } = req.query
  res.end(`Post: ${pid}`)
}
```

## 출처

- [Next.js 공식문서](https://nextjs.org/docs/api-routes/introduction)
