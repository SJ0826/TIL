# 생성자 함수 & arrow 함수

## 생성자 함수 
생성자를 만드는 방식으로 함수를 선언할 수 있는 방법이 있습니다.<br>
```
const sum = new Function('a', 'b', 'c', 'return a + b + c'); 

console.log(sum(1, 2, 3)); 
```
* `new Function`이라는 키워드를 이용한다.<br><br>

* 매개변수를 지정할 땐 문자열로 지정한다.<br><br>

### function과 new Function의 차이점

function은 리턴값이 전역변수가 아닌 지역변수에 접근하지만, <br>
new Function은 지역변수가 아닌 전역변수에 접근합니다.<br><br>

**funtion**

```
{
    const a= 2;

    const test = function() {
        return a; //return이 전역변수가 아닌 지역변수에 접근
    };

    console.log(test());
}
```
결과<br>
`2`<br><br>

**new Fuanction**

```
globalThis.a = 0; //전역변수
{
    const a =1;

    const test = new Function('return a'); // return값이 지역변수가 아닌 전역변수에  접근.

    console.log(test());
}
```
결과<br>
`0`

### 생성자 함수를 이용하여 새로운 객체를 만들어내는 방법

매개변수를 인자로 하여, 인자로 넣어준 매개변수를 객체가 프로퍼티로 가지게 합니다.<br>
```
function Person(name, age) { //name과 age를 인자로 함. 인자로 넣어준 name과 age를 객체가 프로퍼티로 가지게 함.
    console.log(this);
    this.name = name;
    this.age = age;
}


const p = new Person('Mark', 37);

console.log(p, p.name, p.age); 
```
결과<br>
```
Person {} 
Person { name: 'Mark', age: 37 } Mark 37`
```

## arrow 함수
arrow함수는 함수 표현식보다 단순하고 간결한 문법으로 함수를 만들 수 있는 방법입니다.<br><br>

```
const hello3 = (name, age) => {
    console.log('hello3', name, age);
}
```
> 매개변수 name, age의 값을 받아 값을 console.log로 반환하는 함수를 hello3에 선언한다.

* arrow함수는 항상 익명함수 방식으로 선언합니다.<br><br>

* 매개변수가 하나일 때, 괄호는 생략 가능합니다.
<br><br>

* arrow함수는 this를 사용하지 않기 때문에 생성자함수를 생성할 수 없습니다.<br><br>


## 출처
* 패스트캠퍼스