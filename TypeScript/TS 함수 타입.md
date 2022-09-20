# TS 함수 타입

타입 스크립트는 함수에 타입을 정의할 수 있다.

### 함수의 파라미터 타입을 정의하는 방식

```
function sum(a: number, b: number) {
  return a + b;
}

sum(10, 20);
```

함수 `sum`의 파라미터의 타입을 `number`로 지정했다.

### 함수의 반환 값에 타입을 정의하는 방식

```
function add(): number {
  return 10;
}
```

함수 `add`의 반환 값을 `number`타입으로 지정했다.

### 함수에 타입을 정의하는 방식

```
function sum2(a: number, b: number): number {
  return a + b;
}
```

함수 `sum2`의 파라미터와 반환 값에 `number`타입을 지정했다.

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
