# useReducer
### : useState처럼 State를 관리하고 업데이트 할 수 있는 Hook

`useReducer`은 컴포넌트 상태 업데이트 로직을 컴포넌트에서 분리시킬 수 있다.

업데이트 로직을 분리하여 컴포넌트 외부에 작성해 코드의 최적화를 이룬다.

## useReducer 구조

```
const [number, dispath] = useReducer(reducer, initialState, init);

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
    return state + 1;
    case 'DECREMENT':
    return state - 1;
    default:
      return state;
  }
}

```
`action`이라는 객체를 기반으로 상태를 업데이트 한다.

* `dispath`: `reducer`함수를 실행시키고 `action`을 발생시킨다.
* `action`: 업데이트를 위한 정보를 가지고 있다.



## 출처
* 패스트캠퍼스 for velopert
    
