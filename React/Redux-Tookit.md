# Redux toolkit
리액트 환경에는 수많은 상태관리 방법이 있다.
리액트에 이미 내장되어 있는 Context API가 있으며, 이외에도 다양한 라이브러리들이 상태관리를 도와준다.
그럼에도 불구하고 리덕스가 많은 개발자들에게 사용되고 있는 이유는 무엇일까.

## Context API vs Redux

사실 Context API와 Redux는 비교대상이 아니다.
Context는 수단일 뿐, 상태관리 자체는 `useState`와 `useReducer`이 하고 있다.
Context API와 Redux의 가장 큰 차이점은 **성능 최적화**에서 보여진다.
Context API는 성능 최적화가 이루어지지 않아 특정값을 의존하는 경우, 해당하는 특정값이 아닌 다른 값이 변경될 때도 컴포넌트가 리렌더링이 된다.
반면 Redux는 의존하지 않는 값이 바뀌게되면 그 값에 영향을 받지 않고 리렌더링이 발생하지 않는다. 
따라서 Context API를 사용할 경우에는 컴포넌트의 분리가 중요하다.

## Redux tookit 시작하기
### Installation
CRA를 사용하는 경우
```
# Redux + Plain JS template
npx create-react-app my-app --template redux

# Redux + TypeScript template
npx create-react-app my-app --template redux-typescript
```

존재하는 앱에 추가하는 경우
```
# NPM
npm install @reduxjs/toolkit
# Yarn
yarn add @reduxjs/toolkit
```

### Redux toolkit에 존재하는 API
#### `configureStore()`
* `createStores`를 감싸서 간단한 configuration 옵션들과 기본값을 제공한다. 
* 자동으로 사용자의 slice reducers를 합쳐서 사용하는 middleware가 무엇이든 추가한다.

#### `createReducer()`
* 상태가 바뀌기 전에 사용자가 룩업 테이블을 제공하게 한다.
> lookup table? 주어진 연산에 대해 미리 계산된 결과들의 집합(배열)
* 자동으로 `immer`라이브러리를 사용해서 간단한 immutable 업데이트를 작성하게 한다.
#### `createAction()`
* 주어진 액션 타입에 대해 string타입으로 액션함수를 발생시킨다.
* 이 함수는 `toString()`이 내장되어 있어, 상수 타입을 대신해서 쓰인다.
### `createSlice()`
* reducer 함수들, slice 이름, 초기 state 값을 허용하여 자동으로 slice reducer를 생성한다.
#### `createAsyncThunk`
* string 타입의 액션과 프로미스를 반환하는 함수를 받아들인다.
* 자동으로 slice reducer를 생성한다.
#### `createEntitiyAdapter`
* 일련의 재사용 가능한 리듀서와 스토어 안에 데이터를 관리하기 위한 selectors를 생성한다.

## RTK Query
RTK Query는 `@reduxjs/toolkit` 패키지에 추가되어 있는 부가적인 옵션이다.
API 인터페이스를 정의하기 위해 데이터를 **fetching**하고 **caching**하는 간단하지만 강력한 툴셋을 제공한다.
redux toolkit을 사용하는것에 있어 필수적인 과정은 아니지만 API를 사용할 경우 사용하면 편리할듯 하다.

### RTK Query에 포함된 API들
#### `createApi()`
* RTK Query의 핵심적인 기능
* 데이터를 fetching하고 변환하는 방법을 포함해서 엔드포인트를 정의하고 엔드포인트로부터 데이터를 검색하는 방법을 허용한다.
> endpoint? 컴퓨터 네트워크에 연결하고 컴퓨터 네트워크와정보를 교환하는 물리적 디바이스

#### `fetchBaseQuery()` 
* 요청을 단순화하는 것을 목표로 하는 `fetch`를 감싼다. = 데이터 fetching을 단순화하기 위해 사용된다.
* Redux toolkit 공홈은 `createApi`에서 `baseQuery`를 사용하는 것을 추천한다.

#### `<ApiProvider /> `
* 아직 **Redux Store가 없는 경우** 사용할 수 있다.

#### `setupListeners()` 
* `refetOnMount`와 `refetchOnReconnect`를 위해 사용되는 유틸리티

## 타입스크립트와 RDK 시작하기

### Redux Toolkit 초기 설정
#### app/store.ts
```
// app/store.ts

import { configureStore, ThunkAction, Action } from '@reduxjs/toolkit';
import counterReducer from '../features/counter/counterSlice';

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});

export type AppDispatch = typeof store.dispatch;
// 타입 에러를 막기 위해 스토어 설정 파일에서 직접 내보내고다른 파일로 직접가져오는 것이 안전하다.
export type RootState = ReturnType<typeof store.getState>;
export type AppThunk<ReturnType = void> = ThunkAction<
  ReturnType,
  RootState,
  unknown,
  Action<string>
>;

```
#### app/hooks.ts
사용하는 훅들의 타입을 지정해야 한다.
`RootState`와 `AppDispatch`의 타입은 각각 컴포넌트에서 import해서 사용하는 것이 가능하지만,

**`useDispatch`와 `useSelector`는 타입이 지정된 훅으로 사용하는 것이 더 좋다.**

* `useSelector`의 경우,  매번 `(state: RootState)`의 타입을 지정해줄 필요가 없다.
* `useDispatch`의 경우, 기본 `Dispatch`는 thunk를 알지못해서 thunk middleware 타입이 포함된 스토어에서 커스터마이징된 `AppDispatch` 타입을 사용해야한다. `useDispatch`를 추가하면 필요할때 `AppDispatch`를 가져올 수 있다.

이 훅들은 타입이 아니라 변수이기 때문에 store 파일이 아니라 hooks파일에 지정해야한다. 이렇게 hooks파일에 지정해서 필요할때 마다 component파일에서 import해올 수 있다.

```
// app/hooks.ts
import { TypedUseSelectorHook, useDispatch, useSelector } from 'react-redux';
import type { RootState, AppDispatch } from './store';

// Use throughout your app instead of plain `useDispatch` and `useSelector`
export const useAppDispatch = () => useDispatch<AppDispatch>();
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;

```

## Application 사용

### Slice State와 Action Types
각각 slice 파일은 초기 state value에 대한 타입을 지정해서 `createSlice`가 각각 리듀서의 `state`에 대한 타입을 추론할 수 있다.

initial state type을 미리 지정하고 initial state 객체를 생성한다.

```
// slice state 타입 정의
export interface CounterState {
  value: number;
  status: "idle" | "loading" | "failed";
}

// initial state 객체 생성
const initialState: CounterState = {
  value: 0,
  status: "idle",
};
```

#### createSlice로 slice 생성
createSlice는 name, initialState, reducers가 있다. 
* `name`: action앞에 붙어 다른 slice의 action들과 중복을 피한다.
* `initialState`: 미리 생성한 initialState가 들어있다. 
* `reducer`: reducer는 action 역할을 하고 state의 변화를 담당한다. `immer.js`를 내장하고 있어 state값을 자동으로 return한다.
```
const counterSlice = createSlice({
  name: "counter",
  initialState,
  reducers: {
    increment: (state) => {
      state.value += 1
    },
    decrement: (state) => {
      state.value -= 1
    },
    incrementByValue: (state, action: PayloadAction<number>) => {
      state.value += action.payload
    },
  },
})
```

#### export
slice 내의 actions과 reducer를 export한다.
// export actions
export const { increment, decrement, incrementByValue } = counterSlice.actions
// export default slice.reducer
export default counterSlice.reducer

### Store 생성
store에는 state와 dispatch할 함수들이 들어있다. 
타입스크립트를 사용하고 있다면 각각 state와 dispatch의 타입을 지정해 주어야 한다.
* store 생성 명령어: `configureStore`

```
import { configureStore } from "@reduxjs/toolkit"
import CounterReducer from "../features/counter/counter"

export const store = configureStore({
  reducer: {
    counter: CounterReducer,
  },
})

// store와 dispatch의 타입
export type RootState = ReturnType<typeof store.getState>
export type AppDispatch = typeof store.dispatch
```

### Provider 생성
Provider은 store와 app을 연결해서 컴포넌트들이 store에 있는 state나 dispatch를 사용할 수 있게 한다.
가장 상위 컴포넌트에 store를 연결하면 하위 컴포넌트에서도 store를 사용할 수 있다.

```
// index.tsx
import {Provider} from "react-redux"
import {store} from './app/store'

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
    <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);
```

### Hooks 생성: useSelector, useDispatch
store안의 state와 dispatch를 쓰기 위해 useSelect와 useDispatch를 사용해 커스텀 훅을 만든다.

```
// src/app/hooks.ts

import { useDispatch, useSelector, TypedUseSelectorHook } from "react-redux"
import { AppDispatch, RootState } from "./store"

export const useAppDispatch = () => useDispatch<AppDispatch>()
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector
```

### 컴포넌트 안에서 사용하기

```
import React, { useState } from 'react'
import { useAppDispatch, useAppSelector } from '../../app/hooks'

import {increment, decrement, incrementByValue} from './counter'

function CounterView() {
  // 설정한 hook들을 적용
    const count = useAppSelector(state => state.counter.value)
    const dispatch = useAppDispatch()
  // useState로 num값 관리
    const [num, setNum] = useState<number>(0); 
    const handleChange = (e:React.ChangeEvent<HTMLInputElement>) =>{
        setNum(parseInt(e.currentTarget.value))
    }

    return (
        <>
        <div style ={{display : 'flex', justifyContent :"center", alignContent : "center"}}>
        // 버튼이 눌리면 import해온 함수들이 dispatch된다.
            <button onClick ={()=>dispatch(decrement())}>-1</button>
            <h1 style = {{margin : "3em"}}>{count}</h1>
            <button onClick ={()=>dispatch(increment())}>+1</button>  
        </div>
        
        <div>
            <input type="number" onChange = {handleChange}/>
            <button onClick={()=>dispatch(incrementByValue(num))}>+{num}</button>
        </div> 
    </>
    )
}
export default CounterView
```

## 출처
* [Redux tookit 공식 페이지](https://redux-toolkit.js.org/tutorials/overview)
* [doobaloper.log-Redux-Toolkit이란?](https://velog.io/@gsh723/%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC-Redux-Toolkit-%EC%9D%B4%EB%9E%80)