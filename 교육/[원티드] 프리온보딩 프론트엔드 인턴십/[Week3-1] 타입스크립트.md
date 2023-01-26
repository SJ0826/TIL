# 타입스크립트 :sailboat:

## 타입스크립트

### 📝 타입스크립트의 정의와 사용 이유

처음에는 단순했던 자바스크립트 생태계가 복잡해졌습니다. 자바스크립트를 이용해 서버 애플리케이션을 개발하고 다양한 프레임워크를 통해서 모바일 애플리케이션도 개발 가능한 생태계가 형성되었습니다. 이에 따라 자바스크립트를 이용해서 개발하는 애플리케이션의 규모도 점점 증가하게 되었습니다.

타입스크립트는 타입문법을 추가해서 만든 진화된 슈퍼셋입니다. 점점 타입스크립트의 수요도가 늘었고 이제는 필수가 되고 있는 추세입니다.

#### 타입스크립트의 사용 이유

타입스크립트는 강타입 언어입니다.

> 강타입? 타입이 강하게 제약되어 있다.

모든 변수를 선언하는 시점부터 변수의 타입을 지정하고 지정된 값을 바꾸지 못합니다. 이러한 강타입언어를 정적타입언어라고 합니다.
타입스크립트는 다른 기계어와 다르게 자바스크립트로 컴파일됩니다. 따라서 자바스크립트가 쓰일 수 있는 모든 곳에 사용할 수 있습니다.

#### 1. 안정성

타입스크립트는 정적타입 언어, 컴파일 언어입니다. 제약을 두기 때문에 권장되지 않은 코드로 작성할 확률을 줄일 수 있습니다.

```ts
let age: number = 1;

age = "2"; // error
```

타입스크립트에서 에러를 감지하고 개발자에게 피드백을 전달합니다.
타입스크립트의 에러 발생시점은 번역과정, 즉 컴파일 과정에서 잡히기 때문에 유저가 사용하는 과정전에 타입에 대한 에러를 잡을 수 있습니다.

#### 2. 표현력

타입스크립트는 변수에 제약을 거는것뿐만이 아닙니다.
타입스크립트를 사용하면 자바스크립트로는 할 수 없는 표현할 수 있는 범위가 증대됩니다.

타입은 **추상**과 **구체**를 구분지을 수 있습니다.

> 추상? 코드의 겉으로만 보이는 동작 (What), 구체? 동작을 하기 위해 하는 구체적 내용 (How)

```ts
interface Storage {
  setItem: (key: string, item: string) => undefined;
  getItem: (key: string) => string;
}

const localStorage: Storage = {
  // implement
};
const sessionStorage: Storage = {
  // implement
};

function saveToken(storage: Storage, token: string) {
  storage.setItem("access_token", token);
}

saveToken(localStorage, "JWT");
saveToken(sessionStorage, "JWT");
```

개발자는 위 함수만 보고 인자의 타입과 리턴값의 타입만 보고 어떤 동작을 하는지 유추할 수 있습니다.
또한 코드의 자동완성되기 때문에 표현력이 증대된다고 할 수 있습니다.

### 📝 타입스크립트 활용법

#### 타입 지정 방법

1. 명시적으로 지정하기

```ts
let age: number = 1;

function sum(x: number, y: number): number {
  return x + y;
}

// 화살표 함수
const sum = (x: number, y: number): number => {
  return x + y;
};
```

2. 자동 추론 방법

```ts
function sum(x: number, y: number): number {
  return x + y;
}

// 화살표 함수
const sum = (x: number, y: number): number => {
  return x + y;
};
```

#### 기본적인 타입

1. `string, number, boolean`
2. `any`

   - 어떤 타입도 지정될 수 있다.
   - 사실상 자바스크립트와 동일하기 때문에 확실히 안전함을 보장할 때를 제외하고 가급적 활용 X

3. 배열

```ts
const numbers: number[] = [1, 2, 3];

const numbers: Array<number> = [1, 2, 3]; // 제네릭 문법 이용
```

4. 튜플

```ts
const point: [number, number] = [1, 1];
```

    * 불변 배열
    * length와 각 element의 타입이 고정되어 있는 배열

5. 객체

```ts
const point: { x: number; y: number } = { x: 1, y: 1 };

const point: { x: number; y: number } = { x: 1 }; // y 프로퍼티가 없음, 에러
```

6. Optional

```ts
const point: { x: number; y?: number } = { x: 1, y: 1 };

const point: { x: number; y?: number } = { x: 1 }; // y 프로퍼티가 옵셔널, 에러 발생 X
const point: { x: number; y?: number } = { x: 1, y: "1" }; // y의 value가 다름, 에러

function sum(x: number, y?: number) {
  return x + (y || 0);
}
```

    * 값이 없을수도 있지만 있다면 타입을 지정

7. Type Alias

```ts
type Point = { // 타입 선언: 객체안에 x와 y라는 타입이 있다.
	x:number,
	y:number
};

const startPoint:Point = {x:1, y:1};

const endPoint:Point = {x:10 y:15};
```

    * 커스텀 타입
    * 변수처럼 선언해서 저장한뒤 활용
    * 어떤 형태의 타입도 지정할 수 있음

8. Interface

```ts
interface Point = {
	x:number,
	y:number
};

const startPoint:Point = {x:1, y:1};

const endPoint:Point = {x:10 y:15};
```

    * 객체 타입만 지정 가능

> 객체 타입을 지정할 때는 Type Alias를 쓰나요, Interface를 쓰나요?
> 개개인마다 기준을 세우는게 좋습니다.
> 예를들어 interface는 말 그대로 추상적인 형태를 표현할 때 사용합니다.

Q. 함수의 프롭스 객체 타입 -> type alias

#### Advanced Type

1. literal type

```ts
let age: number = 1;
age = 5; // OK

// -----

let age: 3 = 3;
age = 5; // Error!

let name: string = "yeonuk";
name = "yeonwook"; // OK

// ----

let name: "yeonuk" = "yeonuk";
name = "yeonwook"; // Error!

// literal type으로 추론

const age = 1;
const name = "yeonuk";
```

    * 범용적인 타입이 아닌 정확한 형태의 값을 타입으로 지정할 수 있다.

2. as const

```ts
const numners as const = [1,2,3]
numbers.push(4) // error! numbers라는 객체는 readonly(읽기 전용)상태이기 때문.

const theme = {
  gray:"#999",
  black: "#000"
} as const // readonly

background-color: theme.gray // vscode 상에서 색상코드가 보여지기 때문에 표현력이 증가
```

    - 가변적인 값(ex. 객체)의 타입을 지정해 상수로 사용

3. Union

   - Union === 타입의 || 연산자

4. Generic
   문제상황

```ts
function map(array:number[], callback:(...args:any[]) => any;) { // array의 타입을 number 배열로 지정
	const result = [];

	for(const element of array){
		result.push(callback(element));
	};

	return result;
}

map([1,2,3,4], x => x + 1); // Good
map(["hello", "world"], x => x.toUpperCase());
// Type 'string' is not assignable to type 'number'.

```

해결방안

```ts
function map<T>(array:T[], callback:(...args:any[]) => any;) { // array의 타입을 인자처럼 범용적으로 사용
	const result = [];

	for(const element of array){
		result.push(callback(element));
	};

	return result;
}

map<number>([1,2,3,4], x => x + 1); // Good
map<string>(["hello", "world"], x => x.toUpperCase()); // 사용하는 입장에서 타입을 정해서 쓸 수 있다
```

    * 타입을 인자처럼 활용

5. keyof

```ts
type People = {
  name: string;
  age: number;
  gender: "male" | "female";
  hobby: string;
};

type KeyOfPeople = keyof People; // name | age | gender | hobby Union 타입으로 추출
```

    * 객체 타입에서 key들만 Union 타입으로 추출

6. typeof

```ts
const yeonuk = {
  name: "yeonuk",
  age: 1,
  gender: "male",
  hobby: "climbing",
};

type People = typeof yeonuk;
/* 
	{
	  name: string;
	  age: number;
	  gender: string;
	  hobby: string;
	}
*/

// 결합
type KeyOfPeople = keyof typeof yeonuk; // keyof는 타입에만 사용할 수 있기 때문에 결합해서 사용하면 된다.
```

    * 값에서 type 추출

6. norrowing

```ts
function toUpper(arg: string | number) {
  arg.toUpperCase(); // Error! toUpperCase()는 string에만 사용할 수 있기 때문
  /*
		Property 'toUpperCase' does not exist on type 'string | number'.
	  Property 'toUpperCase' does not exist on type 'number'.
	*/
}

// narrowing

function toUpper(arg: string | number) {
  if (typeof arg === "string") {
    arg.toUpperCase(); // OK!
  }
}
```

    * 타입 범위 좁혀나가기

---

## 과제 리뷰

1. 마크업을 로직에 연결하면 안된다.
   마크업이란? html을 다루는 부분
   로직은 UI를 변경시키는 부분.
   유지보수할때 어려움이 생김.
   그렇 어떻게 함? 함수의 인자로 넘겨라 먼소리임

2. 변수명, 불필요한 변수 선언 X
   축약어 지양.
   value라는 추상적인 단어 사용 하지말고 어떤 일을하는 변수인지 알려줘라

3. location state의 잘못된 활용
   useLocation = 페이지를 이동할때 데이터를 넘겨줄 수 있음.
   예시 -> 이전 페이지에서 어떻게 넘어왔는지 의존하게 됨.
   바로 이동한 페이지의 url로 접속하면 어떤 데이터도 갖지 못함.

4. 주석 활용법
   명확하게 마킹해라
   좋은 주석, 나쁜 주석?
   나쁜 주석: 코드에 대해 변명하는 주석, 주석은 낡는다.
   코드를 주석처리하는것도 좋지 않다.
   자신만 알기 때문에 아무도 못지우게 된다.
   좋은 주석: 코드로 설명하지 못하는 부분을 말해주는 주석
   추후에 구현할 사항
   개발자들의 국룰 주석 컨벤현 TODO, FIXME
   // TODO: 에러처리
   // FIXME: 고쳐야할 부분
   배포할때 TODO 주석이 남아있는지 검사하는 스크립트

5. 불필요한 함수 선언 & useEffect 의존성 배열 처리

```js
<li onClick{() => print()} />
<useEffect (() => fetchIssueHandelr(),[fetchIssueHandelr])>
```

6. Drag and Drop 구현시 state값
   구분기분
   state: UI 업데이트에 관한 값, 값이 바뀌면 UI가 리렌더 되야하는 값들 저장할 때
   useRef: DOM 저장할 때

불필요한 함수 호출

useEffect안에 함수를 선언하고 의존성배열을 비우면 의존성을 없앨 수 있다.

6. 다양한 상황처리
   toLowerCase() -> 영어를 사용할 경우 대소문가 구별을 가능하게 했다.

7. 실행방법 & 실행여부 꼼꼼히 확인

8. 딜레이구현
   공 ) 딜레이 처리, 이벤트 중복 방지
9. debounce: **마지막 이벤트**가 발생한 수 특정 시간이 지나면 실행

   - 중복 실행 방지
   - 검색 API 호출 최적화

10. throttle: **특정 시간**마다 한번씩만 실행

    - 중복 실행을 방지하면서, 특정 시간마다 실행을 보장할 수 있음
    - 버튼 클릭 딜레이 최적화
