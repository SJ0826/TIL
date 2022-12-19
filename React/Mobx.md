# Mobx

### : 전역 상태관리 라이브러리

![image](https://user-images.githubusercontent.com/56298540/201336469-6e7ac56d-f039-4409-94a9-a74e864138e6.png)

- 액션이 상태를 변경한다.
- 변경된 상태에 따라 이를 감시하고 있는 계산된 값이 반응한다.
- 경우에 따라서 리액션이 발생하기도 한다.

## Mobx 주요 개념

### 1. Observable State

관찰하고 있는 상태. 상태의 변경이 있으면 Mobx에서 관찰하고 있다가 어떤 부분이 바뀌었는지 파악한다.

### 2. Derivaions(Computations)

Observable state의 변화에 따라 파생된 연산값이다. 필요한 경우에만 업데이트 된다.

### 3. Reactions

Observavle state의 변화에 따른 부가적인 변화이다. 값이 바뀜에 따라 해야할 일을 정하는 함수이다.

### 4. Actions

Observable state가 사용자가 지정한 것을 포함한 모든 변경사항을 말한다.
Mobx는 사용자의 액션으로 발생하는 상태 변화들이 모두 자동으로 Derivations와 Reactions로 처리되도록 한다.

## Mobx와 React를 함께 사용하는 이유

State의 변경사항을 기반으로 최소한의 UI를 업데이트 하는 리액트
+++
절대적으로 필요한 경우에만 state를 변경하는 Mobx
=> **최소한의 state 변경과 최소한의 UI업데이트**로 빠르고 효율적인 인터페이스를 프로젝트에 제공할 수 있다.

## 출처

- 패스트캠퍼스
- [상태관리 라이브러리 - MobX란?](https://is-this-it.tistory.com/79)

* [Mobx 공식문서](https://ko.mobx.js.org/README.html)
