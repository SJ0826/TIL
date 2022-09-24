# 유니온 타입
### : 자바스크립트의 OR 연산자(||)와 같이 A이거나 B이다 라는 의미의 타입
<br>

유니온 타입은 특정 변수나 파리미터에 하나의 타입 이상을 쓸 수 있게 만든다.

키워드 : `|`

```
var seho: string | number | boolean;
```

## 유니온 타입 특징
### 1. 유니온 타입은 타입 가드가 가능하다.
타입 가드: 특정 타입으로 타입의 범위를 좁혀나가는 과정
```
function logMessage(value: string | number) { 
  if (typeof value === 'number') {
    value.toLocaleString();
  }
  if(typeof value === 'string') {
    value.toString();
  }
  throw new TypeError('value must be string or number');
}
logMessage('hello');
logMessage(100);
```


### 2. 유니온 타입은 인터페이스 두개를 연결했을 때 공통된 속성만 제공한다.
유니온 타입은 `OR`연산자와 의미가 비슷하다.

따라서 인터페시스 두개를 연결했을 때 공통된 속성만 제공한다.
```
interface Developer {
  name: string;
  skill: string;
}

interface Person {
  name: string;
  age: number;
}

function askSomeone(someone: Developer | Person) {
   someone.name
   someone.skill // Error
}
```

## 유니온 타입(Union Type)과 인터셉션(Intersection)
인터셉션은 공통된 속성만 제공하는 유니온 타입과는 달리 **인터페이스의 모든 속성을 제공**한다.

따라서 인터페이스를 모두 합친 하나의 타입이라고 정의할 수 있다.

실무에서는 상대적으로 유니온 타입을 더 많이 사용한다.

```
function askSomeone(someone: Developer & Person) {
  someone.name
  someone.skill
  someone.age
}
```

인터셉션은 정의한 타입의 속성을 모두 넘겨야 하는 특징이 있다.
```
askSomeone({ name: '디벨로퍼', skill: '웹 개발', age: 34}); 
```

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
