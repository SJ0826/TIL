# useRef로 컴포넌트 안의 변수 만들기

`useRef`는 DOM요소에 접근할 때도 사용하지만

어떤 값을 계속 기억하고 싶을 때도 사용한다.

`useRef`로 만든 컴포넌트안의 변수는 변경되어도 리렌더링 되지 않는다.

```
function App() {
  ...
  
  const nextId = useRef(4); 

  const onCreate = () => {

    console.log(nextId.current); // 4
    nextId.current += 1;
  }

  ...
}
```
`nextId`의 값이 변경되어도 컴포넌트가 리렌더링되지 않는다.

## 출처
* 패스트캠퍼스 for velopert
    