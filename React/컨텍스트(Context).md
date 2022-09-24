# 컨텍스트

자신은 사용하지 않으면서 밑으로 내려줘야하는 코드가 있을 때 컨텍스트를 사용한다.

컨텍스트를 사용하기 위해서 `createContext`함수를 호출하면 객체가 반환된다.

```
const UserContext = createContext('unknown'); 
```

`createContext`를 호출할 때 초기값을 설정하는데 컴포넌트가 값을 검색할때 해당 값이 없으면 초기값이 사용된다.


객체 안에는 `Provider`와 `Consumer`컴포넌트가 들어있다.

`Provider`에서 `value`에 값을 넣어주면 `Consumer`에서 값을 받아서 처리한다.

`Provider`컴포넌트의 값이 변경되면 하위의 `Consumer`컴포넌트는 다시 랜더링 된다.

중간에 있는 컴포넌트가 렌더링 되지 않아도 `Consumer`컴포넌트는 렌더링된다.
