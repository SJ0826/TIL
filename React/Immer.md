# immer
### : 불변성을 해치는 코드를 작성해도 대신 불변성 유지를 해주는 라이브러리

`immer` 라이브러리를 사용하면 불변성을 유지하면서 새로운 객체를 만들어준다.

## immer 사용하기
1. 커맨드창 혹은 터미널에서 `yarn add immer`를 입력해 라이브러리를 설치한다.

2. `App.js`에 `import produce from 'immer'`를 입력해 해당 라이브러리를 `import`한다.

## immer 구조
```
const 변수 = produce(바꾸고 싶은 값, draft => {
  ...
});
```
* `draft`: 어떻게 바꿀지 알려주는 함수

## 예시
```
import produce from 'immer'

const state = {
    number: 1,
    donChangeMe: 2
};

const nextState = produce(state, draft => {
    draft.number += 1;
});

nextState(); 
```
불변성을 지키지 않으면서 코드를 작성했지만 `produce`함수가 불변성을 유지해준다.

## 출처
* 패스트캠퍼스 for velopert
    


