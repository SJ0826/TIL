# 명시적으로 this를 바인딩 하는 방법

`this`는 함수를 호출할 때 결정된다.<br><br>

하지만 `this`가 가리키는 대상을 명시적으로 바인딩할 수 있다.

## call 메서드

```
Function.prototype.call(thisArg[, arg1[, arg2[, ...]]])
```

`call`메서드는 **호출 주체인 함수를 즉시 실행**하도록 하는 명령이다.<br><br>

- 첫 번째 인자를 `this`로 바인딩한다.
- 이후 인자들은 호출할 함수의 매개변수이다.

```
var obj = {
  a: 1,
  method: function(x, y) {
    console.log(this.a, x, y);
  }
};

obj.method(2, 3);
obj.method.call({ a:4 }, 5, 6);
```

<결과><br>

```
1 2 3
4 5 6
```

`call`메서드의 첫번째 인자로 `this`가 가리키는 `a`값을 4로 변경했다.<br><br>

## apply 메서드

```
Function.prototype.apply(thisArg[, argsArray])
```

- 첫 번째 인자를 `this`로 바인딩한다.
- 두 번째 인자를 배열로 받아 그 배열의 요소들을 호출할 함수의 매개변수로 지정한다.

```
var func = function (a, b, c) {
  console.log(this, a, b, c);
};
func.apply({x:1}, [4, 5, 6]);

var obj = {
  a: 1,
  method: function (x, y) {
    console.log(this.a, x, y);
  }
};
obj.method.apply({ a: 4 }, [5, 6]);
```

<결과><br>

```
{ x: 1 } 4 5 6
4 5 6
```

`call`/`apply` 메서드는 `this`를 예측하기 어렵게 만들어 코드 해석을 방해한다는 단점이 있다.<br>
그럼에도 불구하고 ES5이하의 환경에서는 마땅한 대안이 없어 실무에서 광범위하게 활용된다.

## bind 메서드

```
Function.prototype.bind(thisArg[, arg1, arg2, ...]]])
```

`bind`메서드는 `call`과 비슷하지만,<br>
**즉시 호출하지는 않고 넘겨받은 `this` 및 인수들을 바탕으로 새로운 함수를 반환하기만 하는 함수**이다.

- `this`를 미리 적용한다.
- 부분 적용 함수를 구현한다.

```
var func = function (a, b, c, d) {
  console.log(this, a, b, c, d);
};
func(1, 2, 3, 4);

var bindFunc1 = func.bind({ x: 1 });
bindFunc1(5, 6, 7, 8); // (1)

var bindFunc2 = func.bind({ x: 1}, 4, 5);
bindFunc2(6, 7); // (2)
bindFunc2(8, 9); // (3)
```

(1) `this`를 `{ x: 1}`로 지정했다.<br>
(2)(3) 매개변수로 6, 7을 넘기면 `this`값이 바뀐 겂을 제외하고는 최초 `func`함수에 4, 5, 6, 7을 넘긴 것과 같은 동작을 한다. `this`의 지정과 함께 부분 적용 함수를 구현한 것이다.

## 출처

- 코어 자바스크립트
