# 제네릭(Generics)
### : 타입을 함수의 파라미터에 갖게 하는 문법

제네릭은 함수의 호출하는 시점에 타입을 넘겨준다.

키워드: `T`

```
function logText<T>(text: T): T {
  console.log(text);
  return text;
}
logText('하이'); 
```

제네릭은 다른 언어에서도 많이 쓰인다.

한가지 타입보다 여러 가지 타입에서 동작하는 컴포넌트를 생성하는데 사용되며

재사용성이 높은 컴포넌트를 만들 때 자주 활용된다.

## 왜 제네릭을 사용할까?

단순히 타입을 바꿔 사용하기 위해서 중복코드가 있는 함수를 계속 생성하는 것은 유지보수에 좋지않다.
```
function logText(text: string) {
  console.log(text);
  return text;
}

function logNumber(num: number) {
  console.log(num);
  return num;
}
```
`logText`와 `logNumber`는 같은 내용의 함수지만 파라미터의 타입이 다른 이유로 따로 생성되었다.

```
function logText<T>(text: T): T {
  console.log(text);
  return text;
}

const str = logText<string>('abc');
str.split('');
const login = logText<boolean>(true);
```
이렇게 제네릭을 사용해서 함수의 파라미터값을 지정한다면 

함수를 호출할때 어떤 타입을 지정해도 코드를 진행할 수 있다.

## 어떤 경우에 유니온타입이 아닌 제네릭을 사용할까?

여러 타입으로 함수의 파라미터를 정의할 경우 유니온을 사용하는 방법도 있다.

하지만 유니온타입은 반환값에서 문제가 생긴다.
```
function logText(text: string | number) {
  console.log(text);
  return text;
}

const a = logText('a');
a.split(10); //에러. 타입을 정확히 선언해야만 내장함수를 사용할 수 있음.
logText(10);
```

`text`가 유니온타입으로 `string`과 `number`로 지정되었기 때문에 내장함수를 사용할 수 없는 문제점이 발생한다.


## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
