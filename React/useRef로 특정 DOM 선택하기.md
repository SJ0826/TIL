# useRef로 특정 DOM 선택하기

리액트로 코드를 작성하다 보면 직접 DOM요소에 접근해야하는 경우가 있다.

`useRef`를 사용하며 특정 DOM요소에 접근할 수 있다.

```
const nameInput = useRef(); // DOM 접근
```
변수 혹은 상수에 `useRef`를 호출하면 특정 객체가 생성된다.

```
<input 
  name="name" 
  placeholder="이름" 
  onChange={onChange} 
  value={name} 
  ref = {nameInput} // useRef
/>
```

원하는 곳에 `useRef`를 호출한 변수를 지정한다.

```
  const onReset = () => { // 초기화 기능
   setInputs({
    name: '',
    nickname: ''
   })
   nameInput.current.focus();
  };
```

`onReset`함수를 호출하면 `nameInput`을 지정한 DOM요소에 접근하여 `focus`기능을 호출한다.

## 출처
* 패스트캠퍼스 for velopert
    