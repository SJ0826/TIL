# spread 연산자

`spread`연산자는 ES6문법에서 처음으로 등장했습니다.<br><br>

`spread`연산자는 객체나 배열의 엘리먼트를 요소 하나하나로 펼쳐서 사용할 수 있게 합니다.<br><br>

`...`라는 키워드를 사용합니다.<br><br>

**기존 객체나 배열을 복사하고 추가적인 값을 넣어줄 때** 주로 사용합니다.

```
const first = {
  one: 1
}

const second = {
  ... first, //first의 엘리먼트를 가져옴.
  two: 2
}

consol.log(first);
consol.log(second);
```

<결과><br>

```
{ one: 1}
{ one: 1, two: 2}
```

## 장점

- `spread`연산자는 기존객체를 변경시키지 않고 복사해옵니다.

- 코드의 재사용성이 높아집니다.

## 출처

- 패스트캠퍼스 프론트엔드 강의
