# 타입 호환(Type Compatibility)

### : 타입스크립트 코드에서 특정 타입이 다른 타입에 잘 맞는가

```
interface Developer {
  name: string;
  skill: string;
}

interface Person {
 name: string;
}

var developer: Developer;
var person: Person;

developer = person; // Error
person = developer; 
```

타입 호환은 부분 집합 개념으로 접근하면 쉽다.

에러가 난 코드는 `developer`(왼쪽)가 더 많은 타입을 가지고 있기 때문이다.

오른쪽의 타입이 더 많아야 타입 호환이 이루어진다.

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
