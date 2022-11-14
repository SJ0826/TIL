# JWT (Json Web Token)

### : 유저를 인증하고 식별하기 위한 토큰 기반 인증

## JWT 특징

#### 1. 토큰 자체에 사용자의 권한 정보나 서비스를 사용하기 위한 정보가 포함된다.

데이터가 많아지면 토큰이 커질 수 있으며 토큰이 한 번 발급된 이후 사용자의 정보를 바꾸더라도 토큰을 재발급하지 않는 이상 반영되지 않는다.

#### 2. Restful 과 같은 무상태(Stateless)인 환경에서 사용자 데이터를 주고 받는다.

세션을 사용할 때는 서버에 세션을 저장하지만, JWT는 토큰을 클라이언트에 저장한다. 이후 서버에 요청시 단순히 HTTP 헤더에 토큰을 첨부하는 것만으로도 데이터를 요청하고 응답받을 수 있다.

#### 3. JWT는 JSON 데이터를 Base64 URL-safe Encode를 통해 인코딩하여 직렬화한다.

## JWT 사용 순서

1. 클라이언트 사용자가 아이디, 패스워드를 통해 웹서비스 인증
2. 서버에 서명된(Signed) JWT를 생성하여 클라이언트에 응답으로 돌려주기
3. 클라이언트가 서버에 데이터를 추가적으로 요구할 때 JWT를 HTTP Header에 첨부
4. 서버에서 클라이언트로부터 온 JWT를 검증

## JWT 구조

- JWT의 3구조: **Header, Payload, Signature**

[Header]
JWT에서 사용할 타입과 해시 알고리즘의 종류가 담겨져 있다.

[Payload]
서버에서 첨부한 사용자 권한 정보와 데이터가 담겨있다.

[Signature]
Header, Payload를 Base64 URL-safe Encode를 한 이후 Header에 명시된 해시함수를 적용하고, 개인키(Private Key)로 서명한 전자서명이 담겨있다.

## 출처

- [얄팍한 코딩사전](https://www.youtube.com/watch?v=1QiOXWEbqYQ)

* [hELLO.-JWT의 개념부터 구현까지 알아보기](https://pronist.dev/143)
