# 유틸리티 타입
### : 이미 정의해 놓은 타입을 변환할 때 사용하는 문법

유틸리티 타입을 사용하면 불필요한 타입을 지정하는 것을 줄일 수 있다.

### Partial
: 특정 타입의 부분 집합을 만족하는 타입을 정의할 수 있다.
```
interface Address {
  email: string;
  address: string;
}

type MayHaveEmail = Partial<Address>;
const me: MayHaveEmail = {}; // 가능
const you: MayHaveEmail = { email: 'test@abc.com' }; // 가능
const all: MayHaveEmail = { email: 'capt@hero.com', address: 'Pangyo' }; // 가능
```


### Pick
: 특정 타입에서 몇 개의 속성을 선택하여 타입을 정의한다.

```
interface Hero {
  name: string;
  skill: string;
}
const human: Pick<Hero, 'name'> = {
  name: '스킬이 없는 사람',
};
```

### Omit
: 특정 타입에서 지정된 속성만 제거한 타입을 정의한다.

특정 타입에서 안쓸 속성만 빼고 사용한다. 

```
interface AddressBook {
  name: string;
  phone: number;
  address: string;
  company: string;
}
const phoneBook: Omit<AddressBook, 'address'> = {
  name: '재택근무',
  phone: 12342223333,
  company: '내 방'
}
```

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
