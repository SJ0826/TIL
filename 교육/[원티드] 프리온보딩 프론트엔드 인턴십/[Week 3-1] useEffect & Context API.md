# [Week 3-1] useEffect & Context API :sailboat:

## useEffect의 의존성 배열

### useEffect의 의존성 배열이란?

#### : effect 함수가 의존하고 있는 요소들의 모음

- useEffect에 두번째 인자로 넘기는 배열
- 두번째 인자를 넘기지 않으면 useEffect는 매번 실행되고, 빈 배열을 넘긴다면 첫번째 렌더링 이후에만 실행

### useEffect 의존성 배열을 잘 설정하는 법

- 필요 없는 요소는 배제하고 필요한 의존성을 제대로 넣어줘야 합니다.

  ```js
  function Component() {
    const [count, setCount] = useState(0);

    useEffect(() => {
      document.title = `you clikced ${count} times`;
    }, []);
  }
  ```

- 모든 의존성을 빼먹지 말되 가능하면 의존성을 적게 만들어야 합니다.

```js
// bad
function Component(){
	const [count, setCount] = useState(0);

	useEffect(()=>{
		document.title = `you clikced ${count} times`
	}, []];
}

// good
function Component(){
	const [count, setCount] = useState(0);

	useEffect(()=>{
		document.title = `you clikced ${count} times`
	}, [count]];
}
```

## Context API

### : 리액트에서 제공하는 내장 API

Context API를 사용하면 단계마다 일일이 props를 넘겨주지 않고도 컴포넌트 트리 전체에 데이터를 제공할 수 있습니다.

### 사용법

1. `createContext`
   데이터를 저장해둘 context를 만듭니다.

```js
const UserContext = createContext(null);
```

defaultValue는 Context Value의 초기값이 아닌, 다른 컴포넌트에서 Context에 접근하려고 하지만 Provider로 감싸져 있지 않은 상황에서 사용될 값입니다.

2. `Provider`
   Context 객체에는 Provider라는 프로퍼티가 있으며 이는 리액트 컴포넌트입니다.
   Context에 있는 값을 사용할 컴포넌트를 감싸서 사용합니다.
   - `value`: value에 할당된 값을 Provider 컴포넌트 하위에 있는 어떤 컴포넌트든 접근할 수 있게 합니다.

```js
const UserContext = createContext(null);

const user = { name: "yeonuk" };

<UserContext.Provider value={user}>
  <Child />
</UserContext.Provider>;
```

3. `useContext`
   다른 컴포넌트에서 Context를 통해 공유된 값에 접근할 때 사용합니다.

```js
const UserContext = createContext(null);

const user = { name: "yeonuk" };

<UserContext.Provider value={user}>
  <Child />
</UserContext.Provider>;

function Child() {
  const user = useContext(UserContext);

  return <h1>{user.name}</h1>;
}
```
