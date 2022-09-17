# HTTP 헤더

## HTTP 헤더<br>

`field-name : OWS field-value OWS` (OWS: 띄어쓰기 허용)

field-name은 대소문자 구분이 없다.

헤더에는 HTTP 전송에 필요한 모든 부가 정보가 들어있다.

## 표현

표현: 요청이나 응답에서 전달할 실제 데이터

표현 헤더: 표현 데이터를 해석할 수 있는 정보를 제공

HTTP는 메시지 본문(message body)를 통해 표현 데이터를 전달한다.

### Content-Type

미디어 타입, 문자 인코딩 등 **표현 데이터의 형식**을 설명한다.

<예><br>
HTTP/1.1 200 OK<br>
**Contenet-Type: text/html;charset=UTF-8**<br>
Content-Encoding:gzip<br>
Content-Length: 521

### Content-Encoding

**표현 데이터를 인코딩**한다.

데이터를 전달하는 곳에서 압축 후 인코딩 헤더를 추가하면 데이터를 읽는 쪽에서 인코딩 헤더의 정보로 압축을 해제한다.

<예><br>
HTTP/1.1 200 OK<br>
Contenet-Type: text/html;charset=UTF-8<br>
**Content-Encoding:gzip**<br>
Content-Length: 521

### Content-Language

**표현 데이터의 자연 언어**를 뜻한다.

<예><br>
HTTP/1.1 200 OK<br>
Contenet-Type: text/html;charset=UTF-8<br>
**Content-Language: ko : 한국어로 표현한다.**<br>
Content-Length: 521

### Content-Length

**표현 데이터의 길이**를 뜻한다.

`Transfer-Encoding`안에 모든 정보들이 들어있기 때문에<br>`Transfer-Encoding`(전송 코딩)을 사용하면 Content-Length를 사용하면 안된다.

<예><br>
HTTP/1.1 200 OK<br>
Contenet-Type: text/html;charset=UTF-8<br>
Content-Language: ko<br>
**Content-Length: 521**

## 출처

- [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC)
