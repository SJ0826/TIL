# 프로토타입(prototype)

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

* 굳이 this라는 자기참조변수를 사용하지 않고 prototype으로 변수 p에 hello라는 함수를 할당했다.

```
console.log(p instanceof Person); // P라는 객체가 Person에서 나온 인스턴스인가?
console.log(p instanceof Object); // p라는 객체가 Object에서 나온 인스턴스인가?
```
결과<br>
`true`<br>
`true`<br><br>

* 객체 p가 Person과 Object에서 나온 인스턴스임을 확인할 수 있다.

## 느낀 점
자바스크립트 공부하면서 제일 난관에 봉착했다.<br>
뭔가 알듯 말듯 헷갈리는 개념이다.<br>
강의를 끝나면 모던자바스크립트튜토리얼도 보고 책도 보고 할텐데 그 과정에서 익숙해지며 습득될 수 있도록 꼼꼼히 학습해야겠다.<br>
## 출처

* 패스트캠퍼스 프론트엔드 강의<br><br>

* [생활코딩](https://opentutorials.org/course/743/6573)<br><br>

* [MDN Web Docs](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes)

