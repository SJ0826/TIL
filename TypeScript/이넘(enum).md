# 이넘(enum)

### : 특정한 값들의 집합을 의미하는 자료형

키워드: `enum`
```
enum example {
  A
  B
  C
}
```
## 숫자형 이넘
이넘을 만들때 별도의 값을 지정하지 않으면 숫자형 이넘으로 생성된다.

첫번째 값은 0이 할당되고 두번째 값부터 1씩 증가한다.

```
enum Shoes {
  Nike = 5,
  Adidas 
  
}
```
첫번째만 값을 지정해도 두번째값부터 1씩 증가하여 `Adidas`에는 6이 할당된다.

## 문자형 이넘
이넘의 값을 `string`값으로 할당할 수 있다.
```
enum Shoes {
  Nike = '나이키',
  Adidas = '아디다스',
  
}
```

이넘에 문자와 숫자를 혼합하여 생성하는 것도 가능하다.

## 출처

- [캡틴 판교-타입스크립트 입문 강의](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
