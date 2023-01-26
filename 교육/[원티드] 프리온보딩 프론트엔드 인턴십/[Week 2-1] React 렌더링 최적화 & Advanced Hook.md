# React 렌더링 최적화 & Advanced Hook :sailboat:

## 0. 과제 리뷰

1. 불필요한 파일들은 삭제한다. ex) `App.test.tsx`
2. 사용하지 않는 변수, `import`는 삭제한다.
3. 상수화를 활용한 가독성, 유지보수성 향상
   string타입의 데이터는 길면 가독성도 좋지 않고 유지보수에 좋지 않음

   ```
   const SIGN_IN = "SIGN_IN";
   const SIGN_UP = "SIGN_UP";
   ```

4. 삼항연산자와 조건문의 차이 파악해서 상황에 맞게 쓰기

   - 조건문 -> 문(statement)로 사용
     코드의 분기가 필요할 때는 조건문으로 사용한다.
     > 문? 더이상 나뉠 수 없는 단위 ex) const navigate = useNavigate()

   ```
   const handleClickRegisterChange = () => {
    if (mode === SIGN_IN) {
      setMode(SIGN_UP);
      return;
    }
    setMode(SIGN_IN);
   }
   ```

   - 삼항연산자 -> 표현식(espression)
     값이 필요할 때는 삼항연산자를 사용한다.

   ```

   const handleClickRegisterChange = () => {
   setMode(prevMode => prevMode === SIGN_IN ? SIGN_UP : SIGN_IN)
   };

   ```

5. 변수명만보고 명확한 정보 유추할 수 있게 문법에 맞춰 쓰기
6. state의 최소집합 찾기
   불필요한 state는 빼버리기. 진짜 필요한 state만 남긴다.
   state가 아닌 함수로 만들어서 렌더링될때마다 계산해서 쓸 수 있음
7. `async-await` 동작 이해하고 사용하기
   무의미한 catch 활용
   `catch`안에서 잡아서 던지기만 하지말고 에러처리를 해야한다.
8. 다른 문맥끼리는 공백으로 구분하기, 일관성 있는 포맷팅
9. 코드 작성 순서
   `import` 순서도 지키면 좋다. 팀 컨벤션에 추가하기
   Styled Component는 아래에
   상수선언 한두줄 아니면 밑에
10. 스타일링 방식 혼용 지양
    `div`에 `width: 100%` 는 불필요한 코드

## 01. React 렌더링 최적화 & Advanced Hook

#### 렌더링이란?

화면에 특정한 요소를 그리는 것입니다. 즉, DOM요소를 계산하고 그려내는 것입니다.

- 명령형 개발: 바닐라 자바스크립트를 사용해서 직접 DOM에 접근하고 수정하는 것.
- 선언적 개발: 애플리케이션에서 보여주고 싶은 핵심 UI를 선언하기만 하면 실제로 DOM을 조작해서 UI를 그려내고, 변화시키는 일은 라이브러리나 프레임워크가 대신 해주는 방식

리액트는 선언형으로 실제 렌더링 과정은 리액트에서 진행되면 개발자는 UI를 설계하는 것에 집중합니다.

#### 리액트에서 리렌더링이 되는 시점

state는 UI와 상태(state)를 연동시키기 위해 사용합니다. 이렇게 UI와 연동된 state가 변할때마다 리렌더링이 발생합니다. 해당 컴포넌트와 하위에 있는 모든 컴포넌트가 리렌더링 됩니다.

#### 리액트의 렌더링 과정

1. 이전에 렌더링된 기존 컴포넌트의 UI를 재사용할지 확인한다.
2. 함수컴포넌트: 컴포넌트 함수를 호출 / Class컴포넌트: `render`메소드 호출
3. 2의 리턴값으로 새로운 VirtaulDOM을 생성한다.
4. 이전의 VirtualDOM과 새로운 VirtualDOM을 비교해서 실제 변경된 부분만 DOM에 적용한다.

4번에 해당하는 과정을 리액트에서 자체적으로 해주는 렌더링 최적화 과정입니다.
이 과정에서 개발자는 따로 최적화를 수행할 수 없습니다.

개발자가 수행할 수 있는 최적화는 다음과 같습니다.

1. 기존 컴포넌트 UI를 재사용할지 확인한다.
   재사용한다면 새롭게 컴포넌트를 호출해서 렌더링하지 않고 이전 결과값을 그대로 사용합니다.
2. 2결과를 통해서 새로운 VirtualDOM을 생성한다.
   컴포넌트 함수가 호출되면서 만들어질 VirtualDOM의 형태를 비교적 차이가 적은형태로 만들어지도록 html css를 좀 더 효율적으로 작성합니다.

## 02. 기존의 컴포넌트의 UI를 재사용할 지 판단하는 방법

state가 변하면 해당 컴포넌트와 하위 컴포넌트까지 리렌더링합니다.
UI가 실질적으로 변했는지 검사하는 것 자체가 비효율적이라 리액트는 하위 컴포넌트까지 통으로 리렌더링합니다.
이 과정에서 컴포넌트가 리렌더링 되어야 할지 아닐지에 대한 여부를 개발자에게 넘기는 방법이 있습니다.

### React.memo

```js
const MyComponent = React.memo(function MyComponent(props) {
  /* render using props */
});
```

React.memo를 사용하면 무조건 하위 컴포넌트를 렌더링하지 않고 이전 `props`와 현재 `props`가 변했을때만 렌더링합니다. 값이 변하지 않았다면 이전의 결과를 재사용합니다.

`props`의 비교는 기본적으로 얕은 비교 (shallow compare)로 진행됩니다.
얕은 비교로 하지 않고 다른 로직을 사용하고 싶다면, 변화를 판단하는 함수를 인자로 받도록 설정할 수 있습니다.

```js
function MyComponent(props) {
  /* render using props */
}

function areEqual(prevProps, nextProps) {
  /*
  true를 return할 경우 이전 결과를 재사용
  false를 return할 경우 리렌더링을 수행
  */
}

export default React.memo(MyComponent, areEqual);
```

두번째 인자로 `true`또는 `false`를 리턴하는 함수를 작성합니다.
`true`를 리턴하면 무조건 리렌더링하지 않습니다.

### memo의 잘못된 활용

`props`는 객체 형태로 표현되는데 매 렌더링마다 새롭게 생성됩니다. 따라서 `props` 객체 자체를 비교하는 것은 의미가 없습니다.
`props`자체가 아니라 안에 있는 **`property`들을 비교**해야 합니다.

```js
<Component name="foo" hello="world" />

<Component name="bar" hello="world" />

const areEqual = (prevProps, nextProps) => {
	if(prevProps.name !== nextProps.name) return false;
	if(prevProps.hello !== nextProps.hello) return false;

	return true;
}
```

## 03. Memoization

리액트에서는 제공된 API를 통해서 특정한 값을 저장했다가 재사용할 수 있습니다.

### useMemo

useMemo는 **값**을 memoization하는 함수 입니다.

```js
// useMemo(callbackFunction, deps]

const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

- 첫번째 인자: 콜백함수, 이 함수에서 리턴하는 값이 저장된다.
- 두번째 인자: 의존성 배열, 배열에 있는 값이 하나라도 변경되었다면 새로운 값을 다시 계산한다.

### useCallback

```js
const memorizedFunction = useMemo(() => () => console.log("Hello World"), []);

const memorizedFunction = useCallback(() => console.log("Hello World"), []);
```

useCallback **함수**을 memoization하는 함수 입니다.

### 언제 memoization을 할까?

무조건 memoization을 하는 것이 좋은 것은 아닙니다. 이전의 값을 저장해두고 함수를 호출하고 의존성 배열을 비교하는 과정이 추가되기 때문입니다.
memoization을 하는 것은 상황에 따라 달라집니다.

1. 새로운 값을 만드는 연산이 복잡할 때
2. 함수 컴포넌트의 이전호출과 다음 호출 간 사용하는 값의 동일성을 보장하고 싶을 때
