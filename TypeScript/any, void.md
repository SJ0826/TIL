# any, void
## any
`any`는 모든 데이터 타입을 통칭한 타입이다.<br>
처음 타입을 정의할 때 `any`로 모든 데이터 타입을 지정하고 코드를 작성하면서 타입을 차근차근 적용하는 것이 정석적인 방법이다.
```
//tsconfig.json
"noImplicitAny": true // 데이터 타입을 비워놓지 말고 any라도 붙여라
```
```
let todoItems: any;
```

## void
함수의 리턴타입을 정의해야 하는데 만약 반환타입이 정해지지 않았다면 `void`로 정의해주는 것이 좋다.
```
function addTodo(todo): void {
  todoItems.push(todo);
}

```

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
