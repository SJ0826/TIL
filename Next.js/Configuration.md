# configuration

Next.js의 configuration을 커스텀하려면 `next.config.js`나 `next.config.mjs`를 생성해야 한다.

`next.config.js`는 Node.js의 모듈이다. (JSON 아님)

`next.config.js`는 Next.js의 서버로 사용되지만 브라우저 build 에 포함되지 않는다.

```
// next.config.js

/**
 * @type {import('next').NextConfig}
 */
const nextConfig = {
  /* config options here */
}

module.exports = nextConfig
```

만약 ECMAScript 모듈이 필요하다면 `next.config.mjs`를 사용한다.

```
/**
 * @type {import('next').NextConfig}
 */
const nextConfig = {
  /* config options here */
}

export default nextConfig
```

## 출처

- [Next.js 공식문서](https://nextjs.org/docs/api-routes/introduction)
