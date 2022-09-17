# HTTP 헤더 정보

## 일반 정보

### From

: 유저 에이전트의 이메일 정보

`From`은 일반적으로 잘 사용되지는 않고 검색 엔진 같은 곳에서 주로 사용한다.

### Referer

: 현재 요청된 페이지의 이전 웹 페이지 주소

A -> B로 이동하는 경우 B를 요청할 때 `Referer: A`를 포함해서 요청한다.

`Referer`를 사용하면 유입 경로를 분석할 수 있다.

### User-Agent

: 유저 에이전트 애플리케이션 정보

유저 에이전트 애플리케이션 정보는 웹 브라우저 정보 등등 클라이언트의 애플리케이션 정보를 뜻한다.

유저 에이전트 애플리케이션을 사용하면 어떤 종류의 브라우저에서 장애가 발생하는지 파악할 수 있다.

### Server

: 요청을 처리하는 ORIGIN 서버의 소프트웨어 정보

예) Server: Apache/2.2.22(Debian)

응답에서 사용한다.

### Date

: 메시지가 발생한 날짜와 시간

예) Date: Tue, 15 Nov 1994 08:12:31 GMT

응답에서 사용한다.

## 특별한 정보

### Host

: 요청한 호스트 정보(도메인)

`Host`는 요청에서 사용하는 필수 값이다.

하나의 서버가 여러 도메인을 처리해야 할 때 사용되는 값이다.

![image](https://user-images.githubusercontent.com/56298540/190856779-682d8891-4d90-4085-aa87-750213d99895.png)

### Location

: 페이지 리다이렉션

웹 브라우저는 3xx 응답의 결과에 `Location`헤더가 있으면, `Location`위치로 자동 이동한다.

### Allow

: 허용가능한 HTTP메서드

`405`(Method Not Allowd)에서 응답에 포함해야한다.

`Allow`: `GET`, `HEAD`, `PUT`

### Retry-After

: 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간

`503` (Service Unavailable)에서 서비스가 언제까지 불능인지 알려줄 수 있다.

예) Retry-After: Fri, 31 Dec 1999 23:59:59 GMT (날짜 표기)

## 출처

- [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC)
