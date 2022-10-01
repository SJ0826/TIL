# 맵드 타입(Mapped Type)
### : 기존에 정의되어 있는 타이을 새로운 타입으로 변환해 주는 문법 

자바스크립트 `map()` API 함수를 타입에 적용한 것과 같은 효과를 가진다.

## 맵드 타입 기본 문법
```
{ [ P in  K ] : T }
{ [ P in  K ] ? : T }
{ readonly [ P in  K ] : T }
{ readonly [ P in  K ] ? : T }
```

## 맵드 타입 예제
```
type Heroes = 'Hulk' | 'Capt' | 'Thor'
type HeroAges = { [K in Heroes]: number }
const ages: HeroAges = {
  Hulk: 33,
  Capt: 100,
  Thor: 1000,
}
```
* `Heroes` 는 `Hulk`, `Capt`, `Thor`라는 키를 유니온 타입으로 가진다.
* `HeroAges`에 `Heroes`의 키의 타입을 `number`로 바꾸는 맵드 타입 문법을 적용했다.
* 상수 `ages`는 키값이 `number`인 `HeroAges`를 타입으로 가진다. 

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
