# URI

## URI란?

<br>

### **URI(Uniform Resource Identifier)**<br><br>

**U**niform: 리소스를 식별하는 통일된 방식<br>
**R**esource: 자원, URI로 식별할 수 있는 모든 것(제한 없음)<br>
**I**dentifier: 다른 항목과 구분하는데 필요한 정보<br>
<br>
"URI는 로케이터(locator), 이름(name) 또는 둘다 추가로 분류될 수 있다."<br>

URL(Resource **Locator**)<br>
: 리소스가 있는 위치를 지정<br>
URN(Resource **Name**)<br>
: 리소스에 이름을 부여한다.
위치는 변할 수 있지만, 이름은 변하지 않는다.
URN 이름만으로 실제 리소스를 찾을 수 있는 방법이 보편화 되어 있지 않음.

## URL 문법

<br>

### **scheme://[userinfo@]host[:port][/path][?query][#fragment]**<br>

ex) http://www.google.com:443/search?q=hello&hl=ko<br><br>

#### schme

- 주로 프로토콜이 사용된다.
- 프로토콜: 어떤 방식으로 자원에 접근할 것인가 하는 규칙 ex) http, https, ftp 등등
- http는 80포트, https는 443포트를 주로 사용, 포트는 생략 가능
- https는 http에 보안 추가(HTTP Secure)

#### userinfo

- URL에 사용자정보를 포함해서 인증
- 거의 사용하지 않음

#### 호스트명(www.google.com)

- 도메인명 또는 IP 주소를 직접 사용가능

#### port(443)

- 접속 포트
- 일반적으로 생략가능, 생략시 http는 80, https는 443

#### path

- 리소스 경로, 계층적 구조
- ex) /home/file1.jpg

#### query

- key = value 형태
- ?로 시작, &로 추가 가능 ex> ?keyA=value&keyB=valueB
- query parameter, query string 등으로 불림, 웹서버에 제공하는 파라미터, 문자 형태

#### fragment

- html 내부 북마크 등에 사용
- 서버에 전송하는 정보가 아님.

## 출처

- [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC)
