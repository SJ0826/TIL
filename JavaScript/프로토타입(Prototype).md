# 프로토타입(prototype)

## 프로토타입이란?

프로토타입의 한국어 뜻은 **원형**입니다.<br><br>

프로토타입은 말 그대로 객체의 원형이라고 할 수 있는 것입니다.<br><br>

Javascript에서는 객체를 상속하기 위하여 프로토타입이라는 방식을 사용합니다.<br><br>

```
function Person(name, age) {
    this.name = name;
    this.age = age;
    //this.hello = function() {
    //    console.log('hello', this.name, this.age);
    //}
}

Person.prototype.hello = function() {
    console.log('hello', this.name, this.age);
}

const p = new Person('Mark', 37);

p.hello();
```

결과<br>
`hello Mark 37`<br><br>

- 굳이 this라는 자기참조변수를 사용하지 않고 prototype으로 변수 p에 hello라는 함수를 할당했다.

```
function Person() {} //Person함수 생성

Person.prototype.hello = function() { //Person의 프로토타입으로 hello 함수 생성
    console.log('hello');
}

function Korean(region) { //Korean 함수 생성
    this.region = region;
    this.where = function() {
        console.log('where', this.region);
    };
}

Korean.prototype = Person.prototype; // 프로토타입을 이용해 부모의 프로퍼티를 자식의 프로퍼티에 할당

const k = new Korean('Seoul'); // 변수 k에 객체 할당

k.hello();
k.where();
```

결과<br>
`hello1`<br>
`where Seoul`<br>

## 프로토타입 장점

프로토타입의 장점은 **함수의 재사용성을 높인다는 것**입니다.<br>

프로토 타입을 사용해서 함수 밖에서 새로운 함수나 값을 선언한다면,<br><br>

새로운 함수나 값을 기존 함수에 할당할 필요없이 `prototype`이라는 키워드 하나로 바로 사용가능하기 때문에 코드가 훨씬 간결해집니다.

### 프로토타입 체인

프로토타입을 이용해 서로 이어져 있는 집합을 **프로토타입 체인**이라고 합니다.<br><br>
위의 코드에 다음과 같은 코드를 이어서 작성합니다.<br>

```
console.log(k instanceof Korean);
console.log(k instanceof Person);
console.log(k instanceof Object);
```

<결과><br>
`true`<br>
`true`<br>
`true`<br><br>

- Korean이 Person을 상속하고, Person이 Object를 상속하므로 true값이 나왔다.<br>

## 느낀 점

자바스크립트 공부하면서 제일 난관에 봉착했다.<br>
뭔가 알듯 말듯 헷갈리는 개념이다.<br>
강의를 끝나면 모던자바스크립트튜토리얼도 보고 책도 보고 할텐데 그 과정에서 익숙해지며 습득될 수 있도록 꼼꼼히 학습해야겠다.<br><br>

8/8<br>
두번째로 프로토 타입을 공부한 날.<br>
이해가 됐다!<br>
처음으로 만난 프로토타입은 대체 그래서 뭐하는 친구일까 싶었는데 답답했던 머리가 뻥 뚫리는 기분을 느꼈다.<br>
공부하는 마음에 부스터를 하나 달고 가는 느낌이다.<br>
매우매우 뿌듯하다.

## 출처

- 패스트캠퍼스 프론트엔드 강의<br><br>

- [생활코딩](https://opentutorials.org/course/743/6573)<br><br>

- [MDN Web Docs](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes)
