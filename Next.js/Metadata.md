# Metadata

### : 데이터에 관한 구조와된 데이터로, 다른 데이터를 설명해주는 데이터

Next.js에서는 메타데이터를 이용해 데이터를 설명할 수 있다.

## Head Component의 Metadata

- title / image /description 등 og(open graph) tag
- icon
- third party script(ex. google-analytics..)

```
import Head from 'next/head';

function IndexPage() {
  return (
    <div>
      <Head>
        <title>
          iPhone 12 XS Max For Sale in Colorado - Big Discounts | Apple
        </title>
        <meta
          name="description"
          content="Check out iPhone 12 XR Pro and iPhone 12 Pro Max. Visit your local store and for expert advice."
          key="desc"
        />
      </Head>
      <h1>iPhones for Sale</h1>
      <p>insert a list of iPhones for sale.</p>
    </div>
  );
}

export default IndexPage;
```

## Script Component의 Metadata

- strategy
- onLoad

## 출처

- 패스트 캠퍼스 Next.js 완전 정복

* [Next.js 공식문서](https://nextjs.org/learn/seo/rendering-and-ranking/metadata)
