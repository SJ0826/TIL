# [Week 2-2] Clean Code와 소프트웨어를 유연하고 확장성있게 만드는 법 :sailboat:

## 01. 관심사의 분리와 SRP, Custom Hook

### 📝 Clean Code

많은 개발자들은 깨끗한 코드, 좋은 코드를 위해 노력합니다.

강의를 듣고 생각한 결과 제가 생각한 좋은 코드의 기준은 다음과 같습니다.

- 내가 아닌 다른 사람이 보고 쉽게 이해할 수 있는 코드

* 클라이언트의 요청에 맞게 바로바로 수정이 가능한 코드

- 트렌드에 맞게 마이그레이션이 가능한 코드

오래 되었다고 무조건 나쁜 코드는 아닙니다. 오래되었지만 트렌드에 맞게 고칠 수 있다면 좋은 코드라고 생각합니다.

### 📝 관심사의 분리 (Seperation Of Concerns)

관심사의 분리는 좋은 코드를 만들기 위한 가장 기본적인 출발점입니다.

관심사는 하나의 목적=모듈=최소한의 단위입니다.

즉, 각 함수나 클래스가 한번에 여러 관심사를 처리하려고 하지 않고, 하나의 관심사만 처리하도록 분리하는 것을 의미합니다.

#### 관심사를 분리하는 이유

- 코드가 수정되어야 할 이유가 한가지만 존재하게 됩니다.
- 소프트웨어의 변화는 필연적이고, 좋은 소프트웨어일수록 기존의 기능을 수정, 확장할 수 있어야 합니다. = 유지보수가 쉬워야 합니다.

> 단일 책임 원칙 (Single Responsibility Principle): 모듈들은 책임(수행해야 하는 동작)을 가지고 있으며 각기 하나의 책임만을 가져야 한다는 원칙

> KISS (Keep It Simple, Stupid): 여러 기능을 포함시키면서 복잡하게 만들면 유지보수가 힘들어지기에, 하나의 기능만 수행하도록 하라는 의미

### 📝 Custom Hook

Custom Hook은 리액트에서 관심사를 분리하는 방법입니다.

#### React의 관심사

1. UI
2. 로직 (UI를 변경시키는 부분)

UI는 실제 코드상에서 JSX라는 형태로 표현됩니다.

UI를 제외한 모든 동작에 관한 코드를 로직이라고 부릅니다.

#### React에서 관심사를 분리하는 법: Presentational - Container

리액트에 있는 컴포넌트를 두가지 계층으로 분리시키는 기법입니다.

- Container 컴포넌트: 로직만 다룬다. JSX에 관한 코드가 전혀 없다. state와 life cycle을 관리한다.
- Presentational 컴포넌트: 눈에 보이는 UI만을 다룬다.

하지만 Hook이 등장한 이후 더이상 Presentational - Container 패턴은 많이 사용하지 않습니다.

#### React에서 관심사를 분리하는 법: Custom Hook

커스텀 훅은 리액트 자체 내장 훅을 이용해서 만든 함수입니다.

- React Hook들을 호출하는 함수여야 한다.
- 함수의 이름은 `use`로 시작해야 한다.

```js
// const LIGHT_MODE = "LightMode"
// const DARK_MODE = "darkMode"

const useMode = (initialValue = true) {
  const [isLightMode, setIsLightMode] = useState(initialValue);

  const isLightMode = useCallback(() => isLightMode, [isLightMode])
  const isDarkMode = () => !isLightMode


  const changeMode = () => useCallback(setIsLightMode((prev) => !prev, [isLightMode]))

  return (
    isLightMode,
    isDarkMode,
    changeMode
  )
};
```

```js
const { isLightMode, isDarkMode, changeMode } = useMode(); // 작성한 커스텀 훅을 사용
```

커스텀 훅을 사용하는 입장에서는 로직의 변화를 신경쓸 일이 없도록 작성합니다.

훅의 로직이 변경되어도 사용하는 쪽의 코드는 변경없이 사용할 수 있어야 합니다.

## 02. 횡단 관심사 (Cross-cutting concerns)

### 📝 횡단 관심사

![image](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/05/cross-cutting-concern.png)
횡단관심사는 여러 서비스에 걸쳐서 동작해야 하는 코드입니다.

module1, module2, module3에서 모두 사용하는 기능을 담당합니다.

프론트엔드에서 사용하는 대표적인 횡단 관심사는 **인증 & 인가**입니다.

횡단 관심사를 잘 처리하는 것은 유지보수에서 굉장히 중요합니다.

예를 들어 인증/인가가 혼재되어 있다면, 모든 모듈을 고쳐야 하는 상황이 발생할 수 있기 때문에 횡단 관심사를 적절히 나눠서 처리하는 것이 중요합니다.

### 📝 HTTP 통신에서 횡단 관심사 처리하기

```js
// App.js

import "./styles.css";

export default function App() {
  const request = () => {
    fetch("https://jsonplaceholder.typicode.com/todos", {
      // Authorization, 인증, 횡단 관심사를 처리
      // 이걸 어떻게 잘 처리할 수 있을까?
      headers: {
        Authorization: "ACCESS_TOKEN",
      },
    });
  };

  return (
    <>
      <h1>Cross Cutting Concerns</h1>
      <button onClick={request}>request</button>
    </>
  );
}
```

- 목적: 통신할 때마다 해야하는 동작을 하나의 모듈로 분리해서 처리
  1. 매 요청마다 Authorization header에 token 넣어주기
  2. baseURL을 설정해서 자동으로 url앞에 넣어주기

모듈을 분리할 때는 함수 혹은 클래스로 나누게 됩니다.

가장 큰 차이점은 클래스는 객체형태로 state를 가질 수 있다는 것입니다.

상태를 가지고 있느냐 없느냐에 따라 함수 또는 클래스를 선택해 모듈을 분리합니다.

위의 코드는 token과 baseURL이라는 상태를 저장해야 하기 때문에 클래스로 만드는 것이 적합합니다.

모듈을 만들때는 쓰는 입장에서 어떤 형태로 쓰일지 생각해야 합니다.

```js
// httpClient.js

class HttpClient {
  #baseURL; // private. 클래스 밖에서 접근할 수 없음 ex) httpClient.baseURL (x)
  constructor(baseURL) {
    this.baseURL = baseURL;
  }
  fetch(endPoint, options = {}) {
    // options를 설정해주지 않았을 때를 대비해서 빈객체를 초기값으로 설정
    // undefined.headers는 에러를 발생시키기 때문
    window.fetch(this.baseURL + endPoint, {
      ...options,
      headers: {
        Authorization: "ACCESS_TOKEN",
        ...options.headers, // header가 뒤집어 씌워지더라도 값을 설정
      },
    });
  }
}

const httpClient = new HttpClient("https://jsonplaceholder.typicode.com/");
const localClient = new HttpClient("localhost: 4000");
export { httpClient };
```

```js
// App.js
import "./styles.css";
import { httpClient } from "./httpClient";

export default function App() {
  const request = () => {
    httpClient.fetch("todos", { method: "POST", headers: { AA: "BB" } });
  };

  return (
    <>
      <h1>Cross Cutting Concerns</h1>
      <button onClick={request}>request</button>
    </>
  );
}
```

baseURL이 달라졌을 경우를 대비해서 consructor을 생성합니다.

consructor를 설정하면 클래스를 직접적으로 바꾸지 않아도 객체를 생성할때 인자를 바꿔주기만 하면 됩니다.
