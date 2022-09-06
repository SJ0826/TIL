# async함수와 await

`async`가 붙은 함수는 반드시 프라미스를 반환하고, 프라미스가 아닌 것은 프라미스로 감싸 반환합니다.

## await

await 문은 Promise가 fulfill되거나 reject 될 때까지 async 함수의 실행을 일시 정지하고,<br><br>
Promise가 resolve되어 fulfill되면 async 함수를 일시 정지한 부분부터 실행합니다.<br><br>
이때 await 문의 반환값은 Promise 에서 fulfill된 값이 됩니다.

```
function p(ms) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(ms);
        }, ms)
    })
}

(async function main() {
const ms = await p(1000);
console.log( `${ms}ms후에 실행된다.`);
})();

```

<결과><br>
`1000ms후에 실행된다.`

## promise 객체가 rejected된 경우

Promise 객체가 rejected된 경우의 처리를 위해 **try catch**를 이용한다.<br><br>
catch 블록은 try 블록 안에서 예외가 발생(throw)하는 경우 무엇을 할지 명시하는 코드를 포함합니다.<br><br>  
try 블록 (또는 try 블록 내에서 호출된 함수) 내의 명령문이 예외를 throw 하면 제어가 catch 블록으로 이동합니다.<br><br>
try 블록에 예외가 발생하지 않으면 catch 블록을 건너뜁니다.

```
 (async function 함수이름() {
    try{...}
    catch (error) {...}
 })();
```

## 장점

- 로직의 코드가 안으로 들어가는 것이 아닌 밑으로 흘러가게 하는 것이 가장 큰 장점입니다.
- `await`는 말 그대로 프라미스가 처리될 때까지 함수 실행을 기다리게 만듭니다. 프라미스가 처리되길 기다리는 동안엔 엔진이 다른 일(다른 스크립트를 실행, 이벤트 처리 등)을 할 수 있기 때문에, CPU 리소스가 낭비되지 않습니다.

## 주의할 점

- 일반 함수에는 `await`를 사용할 수 없습니다.
- `await`는 최상위 레벨 코드에서 작동하지 않습니다.

## 출처

- 패스트캠퍼스 강의<br><br>

- [MDN web docs](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/await)

* [모던 자바스크립트 튜토리얼](https://ko.javascript.info/async-await)
