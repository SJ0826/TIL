# 내부함수에서 this를 우회하는 방법

## 왜 this를 우회해야 할까?

함수로서 호출할 때 그 함수의 내부 `this`가 가리키는 대상은 호출 방법에 따라 바뀐다.<br><br>

- 어떤 함수를 메서드로서 호출한 경우 `this`는 **메서드 호출 주체**(메서드명 앞의 객체)를 참조한다.

- 어떤 함수를 함수로서 호출한 경우 `this`는 **전역객체**를 참조한다.

호출 주체가 없을 때는 자동으로 전역객체를 바인딩하지 않고 <br>
호출 당시 주변의 `this`를 그대로 상속받아 사용하는 것이 <br>
자바스크립트 설계상 스코프 체인과의 일관성을 지키는 방식이다.

## 어떻게 this를 우회해야 할까?

ES5까지는 자체적으로 내부함수에 `this`를 상속할 방법이 없다.<br><br>

가장 대표적인 방법은 **변수를 활용**하는 것이다.

```
var obj = {
  outer: function () {
    console.log(this);
    var innerFunc1 = function () {
      console.log(this);
    };
    innerFunc1();

    var self = this;
    var innerFunc2 = function () {
      console.log(self);
    };
    innerFunc2();
  }
};

obj.outer();
```

<결과><br>
outer 스코프에서 `self `라는 변수에 `this`를 저장한 상티에서 호출한 `innerFunc2`의 경우 `self`에는 객체 `obj`가 출력된다.

## 출처

- 코어 자바스크립트
