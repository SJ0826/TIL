# XML

<center><img src="https://user-images.githubusercontent.com/56298540/215452315-25d01e72-eaa3-414c-b74a-963fb54a930e.png"  width="600" height="600"/></center>

## 01. XML이란?

XML은 열린태그와 닫힌태그로 구성하는 데이터 포맷입니다.

```xml
<?xml version="1.0" encoding="UTF-8"?> // 프롤로그
<CSKnowledgeList>
<CS>
<name>디자인패턴</name> <difficult>5</difficult>
</CS>
<CS>
<name>네트워크</name> <difficult>4</difficult>
</CS>
</CSKnowledgeList>
```

html과 다르게 정해져있는 태그이름이 없으며 최상위 태그는 하나만 사용 가능합니다.

## 02. XML은 언제 사용할까?

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
<url>
<loc>http://www.example.com/foo.html</loc>
<lastmod>2018-06-04</lastmod>
</url>
<url>
<loc>http://www.example.com/abc.html</loc>
<lastmod>2018-06-04</lastmod>
</url>
</urlset>
```

xml은 사이트맵을 작성할 때 사용됩니다.

> 사이트맵이란? 사이트에 있는 페이지, 동영상 및 기타 파일과 그 관계에 관한 정보를 제공하는 파일

사이트맵은 SEO(검색 엔진 최적화)를 위해 사용합니다.

만약 사이트가 너무 크거나 링크가 종속되어 있지 않은 경우 웹 크롤러가 페이지를 누락하는 경우가 있는데

이때 작성한 사이트맵이 크롤러에게 페이지에 대한 정보를 알려줍니다.

---

## 출처

- [CS지식의 정석](https://www.inflearn.com/course/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EB%A9%B4%EC%A0%91-cs-%ED%8A%B9%EA%B0%95)
