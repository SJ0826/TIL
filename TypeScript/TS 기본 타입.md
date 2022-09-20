# TS 기본 타입

TS는 기본 데이터 타입을 정의하는 방식이 JS와 다르다.

### 문자열

```
// JS 문자열
let str = 'hello';

// TS 문자열
let str: string = 'hello';
```

### 숫자

```
// TS 숫자
let num: number = 10;
```

### 배열

```
// JS 배열
//let arr = [1, 2, 3];

// TS 배열
let arr: Array<number> = [1, 2, 3];
let heroes: Array<string> =['Cat', 'Thor', 'Hulk', ];
let items: number[] = [1, 2, 3]; // 객체 리터럴
```

### 튜플

: 배열 인덱스의 타입을 정의한다.

```
// TS 튜플
let address: [string, number] = ['gangnam', 100];
```

### 객체

```
// TS 객체
let obj: Object = {};
//let person: object = {
//  name: 'capt',
//  age: 100
//};
let person: { name: string, age: number} = {
  name: 'thor',
  age: 1000
}
```

### 진위값

```
// TS 진위값
let show: boolean = true;
```

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
