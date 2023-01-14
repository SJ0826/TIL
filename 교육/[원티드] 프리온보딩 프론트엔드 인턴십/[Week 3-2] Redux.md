# Redux :sailboat:

## Design Patten
디자인패턴이란? 소프트웨어를 설계하면서 자주 발생하는 문제에 대한 모법답안입니다.

### 📝 Flux

Flux는 페이스북팀에서 발표한 **단방향성** 디자인 패턴입니다. 

![flux](https://haruair.github.io/flux/img/flux-simple-f8-diagram-1300w.png)

* `Action`: 어떤 변화를 발생시킬지 정의하는 type property와 변화에 필요한 데이터를 담고 있는 객체
* `Dispatcher`: `Action`을 받아와서 모든 Store에 전달하는 역할 수행
* `Store`: 애플리케이션의 데이터를 저장. `Dispatcher`에 전달된 Action에 따라 수정
* `View`: `Store`에 저장된 데이터를 받아 UI로 표현, 유저의 동작에 따라 Action을 생성 

## Redux
리덕스는 Flux 패턴을 근간으로 하는 전역 상태 관리 라이브러리입니다.
### 📝 리덕스의 3가지 원칙
#### 1. Single source of truth
리덕스에서는 모든 상태가 Store라는 **하나의 객체에 저장**됩니다.
```js
{
  visibilityFilter: 'SHOW_ALL', // state 1
  todos: [                      // state 2
    {
      text: 'Consider using Redux',
      completed: true,
    },
    {
      text: 'Keep all state in a single tree',
      completed: false
    }
  ]
}
```
#### 2. State is read-only
Redux에서 State를 직접 변경하는 것은 불가능합니다. State를 변경시키려면 Action객체를 Dispatch를 통해 전달해야 합니다. 모든 변경 요청이 Dispatch를 통해 실행되기 때문에 동시에 데이터를 수정하면 발생하는 race condition 문제 등이 발생하지 않습니다. 
```js
const action = {
	type: 'COMPLETE_TODO',
  index: 1
}

store.dispatch(action)

// ------------------------

store.dispatch({
  type: 'SET_VISIBILITY_FILTER',
  filter: 'SHOW_COMPLETED'
})
```
#### 3. Changes are made with pure function
Action을 통해서 Store를 변경시키는 동작은 **Reducer**라는 순수함수가 담당합니다. 
> 순수함수란? 사이드 이펙트 없이 동일한 Input값을 받았을 경우 동일한 Output을 내는 함수

Reducer는 이전 state 값과 action 객체를 인자로 받아 새로운 state를 생성해 리턴합니다.

```js
function visibilityFilter(state = 'SHOW_ALL', action) { // reducer 1
  switch (action.type) {
    case 'SET_VISIBILITY_FILTER':
      return action.filter
    default:
      return state
  }
}

function todos(state = [], action) { // reducer 2
  switch (action.type) {
    case 'ADD_TODO':
      return [
        ...state,
        {
          text: action.text,
          completed: false
        }
      ]
    case 'COMPLETE_TODO':
      return state.map((todo, index) => {
        if (index === action.index) {
          return Object.assign({}, todo, {
            completed: true
          })
        }
        return todo
      })
    default:
      return state
  }
}

import { combineReducers, createStore } from 'redux'
// root reducer(visibilityFilter, todos)를 통합해서 rootReducer 생성
const reducer = combineReducers({ visibilityFilter, todos })

// root reducer를 통해서 store 생성
const store = createStore(reducer)
```
store가 하나인것 처럼 reducer도 하나만 존재하지만, 프로젝트의 규모가 큰 경우 여러개의 reducer를 통합해서 사용할 수 있습니다.

### 📝 Reducer의 구성요서와 데이터 흐름
#### 1. View
: store의 state를 기반으로 유저에게 보여지는 UI

#### 2. Action
: type property를 가지고 있는 자바스크립트 객체

type property는 어떤 변화가 발생했는지 묘사하는 string입니다. 
Action 객체의 구조는 다음과 같습니다.
```js
{
  type: 'TODO/ADD_TODO',
  payload: "Learn Redux"
}
```
type property는 필수요소이며 이외의 property는 추가적인 데이터가 있을 시 선택요소입니다.

#### 3. Action Creator
: Action을 생성하는 함수
```js
const addTodo = todo => {
	return {
		type: 'TODO/ADD_TODO',
		payload:todo
	}
}
```

#### 4. Reducer
: 이전 state 값과 action 객체를 인자로 받아 새로운 state를 리턴하는 함수 `(state, action) => newState`

1. reducer가 처리할 수 있는 action인 경우
state와 action을 통해서 새로운 state 객체를 만든 뒤 리턴
2. reducer가 처리할 수 없는 action인 경우
기존의 state를 그대로 리턴

```js
const INITIAL_STATE = { value: 0 }

function counterReducer(state = INITIAL_STATE, action) {
  // Reducer가 현재 전달받은 Action을 처리할 수 있는지 판단한다.
  if (action.type === 'counter/increment') {
    // 처리할 수 있을 경우 state와 action을 통해서 새로운 state 객체를 만든 뒤 리턴한다.
    return {
      ...state,
      value: state.value + 1
    }
  }

  // 처리할 수 없는 Action인 경우에는 기존의 state를 그대로 리턴한다.
  return state
}
```

#### Store
: 모든 state를 관리하는 객체

```js
import { countReducer } from 'redux'
// root reducer(visibilityFilter, todos)를 통합해서 rootReducer 생성
const reducer = combineReducers({ countReducer })

// root reducer를 통해서 store 생성
const store = createStore(reducer)

// getState 메서드를 통해 현재 state 획득
store.getState() // {value: 0}
```

#### Dispatch
: Action객체를 Store에 전달

Dispatch를 통해 Action이 전달되면 Store는 Reducer를 통해서 새로운 state를 생성합니다.

```js
store.dispatch({ type: 'counter/increment' })

store.getState() // {value: 1}

store.dispatch({ type: 'counter/increment' })

store.getState() // {value: 2}
```

#### Selectors
: store에서 특정한 state만 가져오기 위한 함수

```js
const selectCounterValue = state => state.value

const currentValue = selectCounterValue(store.getState())

console.log(currentValue) // 2
```


## React-Redux
: Redux와 React를 통합하기 위해 필요한 복잡한 과정을 수행해주는 라이브러리

React에서 Redux를 최적화된 환경에서 사용하기 위해 사용하는 라이브러리입니다.

### 📝 React-Redux에서 제공하는 기능
#### 1. Provider
: React 컴포넌트들에게 Redux Store에 접근할 수 있는 기능을 제공

```js
// 일부 코드 생략

import { Provider } from 'react-redux';
import store from './store/index';
import App from './App';


root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```
#### 2. useSelector
: 컴포넌트에서 Store의 값을 가져오는 함수

```js
import { useSelector } from 'react-redux';

const Counter = () => {
  const count = useSelector((state) => state.value);

  return <h1>{count}</h1>;
};
```

#### 3. useDispatch
컴포넌트에서 action을 store에 보내기 위한 dispatch 함수를 가져오는 함수

```js
import { useSelector, useDispatch } from 'react-redux';

const Count = () => {
  const count = useSelector((state) => state.counter);
  const dispatch = useDispatch();

 const increase = () => {
    dispatch({ type: 'counter/increment' });
  };

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increase}>increment</button>
    </div>
  );
};

export default Count;
```