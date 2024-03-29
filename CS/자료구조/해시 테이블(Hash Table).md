# 해시 테이블 (Hash Table)

![해시 테이블](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb1zOw1%2FbtqL6HAW7jy%2FjpBA5pPkQFnfiZcPLakg00%2Fimg.png)

## 해시 테이블이란?

해시 테이블은 (Key, Value)로 데이터를 저장하는 자료구조입니다.

해싱이라는 과정 동안 어떤 데이터를 해시함수를 사용해 변환해 index로 삼아 key와 value를 저장합니다.

테이블이란 어떤 내용을 일정 순서에 따라 저장한 배열을 뜻하는데 이 배열의 키에 해시 함수를 적용해 고유한 인덱스를 생성합니다.

이렇게 키에 해시 함수를 적용하게 되면 테이블에 빈 공간이 생성이 됩니다.

key와 value의 형식의 데이터 구조를 가지고 있기 때문에 O(1)의 성능을 가집니다.

## 데이터 충돌이 일어난다면?

데이터를 해시 함수를 통해 변환하면 똑같은 자리에 데이터가 중복으로 들어올 수 있습니다.

이런 충돌을 해결하기 위해서 해당 인덱스를 연결리스트로 구성해 데이터들을 연결합니다.

이때는 O(n)의 성능을 가집니다.

## 해시 테이블의 장점과 단점

### 장점

- 빠른 데이터 탐색, 삽입, 삭제를 할 수 있다.

### 단점

- 공간의 효율성이 좋지 않다. 미리 많은 공간을 준비해둬야하고 해시 함수에 따라 공간의 낭비가 극대화될 수도 있고 조금 덜할 수도 있다.

## 출처

- [그림으로 배우는 자료구조와 알고리즘](https://www.inflearn.com/course/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B8%B0%EB%B3%B8)
