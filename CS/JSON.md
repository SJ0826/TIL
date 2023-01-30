# JSON
![JSON](https://nesoy.github.io/assets/posts/20170208/json.PNG)
서버에서 사용하는 언어와 프론트에서 사용하는 언어가 다른 경우가 대부분입니다. 서로 사용하는 언어가 달라도 데이터는 주고 받아야하기 때문에 하나의 포맷을 정합니다. 그 중 대표적인 데이터 포맷이 **JSON**입니다.

 ## 1. JSON이란?
  JSON은 자바스크립트 객체 문법으로 구조화된 데이터를 표현하기 위한 표준 포맷입니다.

  ```js
  let a = `{
    "name" : "kundol", 
    "like" : { "아령" : { "weight" : "10kg", "feature" : "육각형" }, "바나나" : { "color" : "초록색" } }
  }`
```
자바스크립트 객체 문법을 따르기 때문에 `key`와 `value`로 표현됩니다. 

JSON은 문자열이기 때문에 데이터를 사용하려면 `parse`문법을 사용해 객체로 바꿔야 합니다.

```js
JSON.parse(a)
```

### :bulb: JSON 사용시 주의할 점
1. JSON은 순수한 포맷이기 때문에 `key`, `value`만 담으며 메서드는 담을 수 없습니다.
2. 큰 따옴표만 사용해야 합니다.
3. `undefined`는 사용할 수 없습니다.

## 2. JSON의 자료형
* Number
* String
* Boolean
* 배열
* 객체
* null

## 3. JSON의 장점
1. JSON은 텍스트로 이루어져 있어 사람과 컴퓨터가 모두 읽을 수 있습니다. 
2. 프로그래밍 언어와 플랫폼에 독립적입니다. 따라서 서로 다른 시스템간에 데이터를 교환하기 용이합니다.
3. 주로 config파일에 활용되며 가볍습니다.

---

## 출처
* [CS지식의 정석](https://www.inflearn.com/course/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EB%A9%B4%EC%A0%91-cs-%ED%8A%B9%EA%B0%95)