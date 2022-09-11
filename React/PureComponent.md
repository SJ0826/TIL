# PureComponent

리액트는 클래스로 만들 수 있는 `Component`와 `PureComponent`가 있다.

`PureComponent`와 `memo`는 `Component`의 `state`나 `Props`에 변화가 없다면 `render` 함수가 호출되지 않는다.

PureComponent는 `shouldComponentUpdate()` 함수를 구축했다.

`shouldComponentUpdate()`는 이전의 `state`와 `prop`을 업데이트된 `state`와 `prop`을 비교해서 변화가 없으면 업데이트를 하지 않도록 `false`를 리턴한다.

`prop` 안의 객체들의 값이 변경되어도 객체 자체가 변경되지 않는다면 `prop`은 업데이트 되지 않는다.

## 출처

- 드림코딩
