# HTTP 메서드의 속성

![image](https://user-images.githubusercontent.com/56298540/189523705-1051e532-6391-475b-9dcc-be8c0131e9dd.png)

## 안전(Safe)

: 호출해도 리소스를 변경하지 않는다.

## 멱등(Idempotent)

: 한 번 호출하든 여러번 호출하든 결과가 똑같다.<br>자동복구 매커니즘에서 활용된다.

- `GET`: 한 번 조회하든, 두 번 조회하든 같은 결과가 조회된다.
- `PUT`: 결과를 대체한다. 따라서 같은 요청을 여러번 해도 최종 결과는 같다.
- `DELETE`: 결과를 삭제한다. 같은 요청을 여러번 해도 삭제된 결과는 똑같다.
- `POST`: 멱등이 아니다! 두 번 호출하면 같은 결제가 중복해서 발생할 수 있다.

### 재요청 중간에 다른 곳에서 리소스를 변경해버리면?

<예시><br>
사용자1: GET -> username:A, age:20<br>
사용자2: PUT -> username:A, age:30<br>
사용자3: GET -> username:A, age:30 >> 사용자2의 영향으로 바뀐 데이터 조회 >> **멱등이 아님!**<br>
멱등은 외부 요인으로 중간에 리소스가 변경되는 것 까지 고려하지 않는다.

## 캐시가능(Cacheable)

: 응답 결과 리소스를 캐시해서 사용해도 되는가?<br>

- `GET`, `HEAD`, `POST`, `PATCH` 캐시가능
- 실제로는 `GET`, `HEAD` 정도만 캐시로 사용<br>
  `POST`, `PATCH`는 본문 내용까지 캐시 키로 고려해야 하는데, 구현이 쉽지 않음.

## 출처

- [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC)
