# 이벤트 루프 과정

이벤트 루프를 이해하기 전 포인트 체크

1. 자바스크립트는 멀티 스레드를 지원하지 않는다.<br>
2. 따라서 브라우저의 WEP API를 통해서 마치 멀티 스레드가 되는 것처럼 작업을 수행한다.

## 어떻게 자바스크립트의 엔진과 웹 API가 서로 상호작용 할까?

자바스크립트 엔진에 있는 Call Stack과 WEB API들을 순환하며 관찰하는 것을 **이벤트 루프**라고 부른다.<br>
브라우저는 사용자에게 1초동안 60개의 프레임을 보여준다.<br>
즉, 16.7ms동안 업데이트가 일어나야 한다.<br>
이벤트 루프는 매우 빨라 한바퀴 도는데 1ms도 걸리지 않는다.<br>

### 이벤트 루프 순서

1. 브라우저에 이벤트가 발생하면 Microtask Queue 또는 Task Queue또는 Request Animation Frame Queue에 작업이 저장된다.
2. 콜 스택이 비워질 때까지 기다렸다가 콜 스택이 비워지면 작업을 콜 스택으로 이동시킨다.
3. 콜 스택에서 모든 작업을 끝낸 후 렌더링되고 브라우저에 표시된다.
   ![이벤트루프](https://user-images.githubusercontent.com/56298540/185134785-2d060abc-fcc9-4613-bff1-f4693c741e86.jpg)

### 포인트

- 콜스택에서 수행중인 아이는 끝날 때까지 보장이 되기 때문에, 중간에 다른일을 할 수 없고 수행중인 코드 블럭이 끝날때까지 이벤트 루프가 기다린다.

- 콜백함수의 내용은 어떤 순서로 작성되어있든지 상관없다. **자바스크립트 엔진이 콜백에 들어 있는 코드블럭이 다 완료될때까지 기다렸다가 나중에 렌더링이 발생하기 때문**이다!<br>

- 콜스택에 등록할 콜백함수를 작성할 때는 오랫동안 머물지 않게 하는 것이 좋다. loop나 재귀함수등은 조심해서 사용해야한다.

```
const button = document.querySelector('button');
  button.addEventListener('click', () => {
    while(true) { // 콜 스택이 계속되고 있음. 브라우저가 반응하지 않음.
      //repeat
    }
  });
```

> 콜 스택에서 함수가 무한루프되고 있어 브라우저에 에러가 발생한다.

## 함수가 Task Queue에 저장될 경우

1. 브라우저에서 지정된 이벤트가 발생했을때, 콜백함수를 태스크 큐에 넣는다.<br>

2. 웹 API는 콜백함수를 태스크 큐에 넣어준다.<br>

3. 이벤트 루프는 계속 관찰을 하다가 콜 스택에 할일이 남아 있으면 콜스택이 비워질 떄까지 기다린다. <br>
4. 콜스택이 비어서 자바스크립트 엔진이 더이상 일을 하지 않을 떄 태스크 큐에 있는 함수를 콜 스택으로 가져온다.<br>
5. 자바스크립트 엔진이 콜 스택에 들어온 콜백함수를 실행한다.<br>

### 포인트

- 이벤트 루프는 콜스택에 있는 함수를 하나씩만 가져온다.

```
function handleClick() {
      console.log('handleClick');
      setTimeout(() => {
        console.log('setTimeout');
        handleClick(); // 콜스택에 무한으로 추가되어 동일한 내용의 이벤트루프가 반복된다.
      }, 0);
    }

    const button = document.querySelector('button');
    button.addEventListener('click', () => {
      handleClick();
    });
```

콜백함수 내에서 다시 콜백함수를 호출하기 때문에 Task Queue에 무한으로 함수가 추가된다.<br>

## 함수가 Microtask Queue에 저장될 경우

1. 콜 스택에서 프로미스를 만들고 프로미스에 등록된 콜백, 즉 프로미스가 다 수행이 되고나면 실행되는 `then`과 `mutation observer`라는 웹 API에 등록된 콜백이 마이크로 큐에 들어온다.<br>

2. 이벤트루프는 마이크로 태스크 큐에 있는 프로미스 then 콜백을 비어있는 콜스택으로 가져간다.<br>

3. 프로미스 `then`이 끝나면 `mutation obsever`를 콜 스택으로 가져간다.<br>

### 포인트

- 이 과정에서 마이크로 태스크 큐에 새로운 함수가 들어온다면, 나중에 들어온 함수도 모두 끝날때까지 계속 콜스택으로 가지고 와서 수행한다.<br>
- 마이크로 태스크 큐가 텅텅비면 테스크 큐로 넘어간다. <br>
  (태스크 큐와의 차이점: 태스크 큐에서는 아이템 하나만 콜스택으로 보내고 기다린다.)<br>

```
function handleClick() {
  console.log('handleClick');
  Promise.resolve(0) // promise 의 콜백은 Microtask que를 이용한다.
    .then(() => {
      console.log('then');
      handleClick();
    });
}

const button = document.querySelector('button');
button.addEventListener('click', () => {
  handleClick();
});
```

이벤트루프는 마이크로태스크 큐에 등록된 콜백이 모두 빌때까지 기다리기때문에 이벤트루프가 멈춰 브라우저가 반응하지 않는다.

## 함수가 Request Animation Frame Queue에 저장될 경우

Request Animation Frame Queue는 렌더링이 되기 전 브라우저가 콜백함수를 실행하는 것을 보장해준다.<br>

render안의 Request Animation Frame이라는 웹 API를 통해서 콜백을 차곡차곡 등록해 놓으면 브라우저가 업데이트 되기 전에 콜백을 실행해준다<br>
브라우저를 다시 업데이트 할 떄는 render안의 request Animation Frame 에 등록된 콜백들을 거친 후 렌더 트리를 만들고 그 트리를 이용해서 레이아웃을 계산한 뒤에 페인트를 통해서 브라우저에 업데이트를 한 다음에 이벤트루프가 재개된다.<br>

```
const button = document.querySelector('button');
button.addEventListener('click', () => {
  requestAnimationFrame(() => { // 렌더링이 되기 전 브라우저가 콜백함수를 실행하는 것을 보장해준다.
    document.body.style.backgroundColor = 'beige';
  });
  requestAnimationFrame(() => {
    document.body.style.backgroundColor = 'orange';
  });
  requestAnimationFrame(() => {
    document.body.style.backgroundColor = 'red';
  });
})
```

QUE는 FIFO의 구조를 가지고 있기 때문에 마지막에 들어온 코드가 적용이 된다.<br>
최종적으로 빨간색이 적용된 상태에서 렌더트리가 만들어지고 브라우저에 표기가 완료된다.

## 느낀점

자바스크립트 기초 문법을 배울 때 비동기 함수에 대해 이해하기 어려웠다.<br>
오늘 이렇게 이벤트함수에 대해 공부하니 비동기 함수가 어떤식으로 처리되는지 감이 잡히고 이해하기 수월해졌다.<br>
그동안 언어를 공부하면서 엔진에 대해 공부해본적이 없던 것 같은데 아는 것과 모르는 것에 큰 차이가 있다는 것을 새삼 느꼈다.

## 출처

- 드림코딩
