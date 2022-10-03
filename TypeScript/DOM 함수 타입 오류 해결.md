# DOM 함수 타입 오류 해결 방법
타입스크립트 코드에서 `DOM`요소의 타입을 정의할 때 에러가 발생하는 경우가 있다.

```
// app.ts
const confirmedTotal: HTMLSpanElement = $('.confirmed-total'); // Error
```
![image](https://user-images.githubusercontent.com/56298540/193511436-e15097ea-8da2-43e0-a1bc-afa0769e9283.png)

## 에러 발생 이유

`Element`타입이 `HTMLSpanElement`의 프로퍼티 값을 가지지 않는다는 뜻이다.

`confirmedTotal`은 `HTMLSpanElement`타입을 지정하기 전에 `Element`타입으로 정의되어 있었다.

하지만 `HTMLSpanElement`을 지정하자 에러가 발생했다.

타입간에 호환할 수 있는 형태가 아니기 때문에 에러가 발생한 것이다.

`HTMLSpanElement`는 `Element`를 상속한다.

에러 메세지에 있는 것 처럼 `Element`가 가지고 있지 않은 속성이 100개가 넘기 때문에 타입이 호환되지 않아 에러가 발생했다.

## 해결 방법

타입 단언을 사용한다.

```
// app.ts
const confirmedTotal = $('.confirmed-total') as HTMLSpanElement;
```
타입 단언을 사용해서 `$('.confirmed-total')` 타입을 지정했다.

`HTMLSpanElement`로 타입을 지정한 이유는 `confirmed-total`이 `html`코드에서 `span`태그를 사용했기 때문이다.
```
// index.html
<span class="confirmed-total"></span>
```

이처럼 각 태그에 맞게 타입 단언을 하면 에러가 해결 될 수 있다.

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
