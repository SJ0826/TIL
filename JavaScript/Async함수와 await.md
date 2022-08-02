# async함수와 await
await연산자는 Promise를 기다리기 위해 사용됩니다.<br><br>

연산자는 async function내부에서만 사용할 수 있습니다.<br><br>

## await
await 문은 Promise가 fulfill되거나 reject 될 때까지 async 함수의 실행을 일시 정지하고,<br><br>
Promise가 resolve되어 fulfill되면 async 함수를 일시 정지한 부분부터 실행합니다.<br><br>
이때  await 문의 반환값은 Promise 에서 fulfill된 값이 됩니다.

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

로직의 코드가 안으로 들어가는 것이 아닌 밑으로 흘러가게 하는 것이 가장 큰 장점입니다.

## 출처

* 패스트캠퍼스 강의<br><br>

* [MDN web docs](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/await)