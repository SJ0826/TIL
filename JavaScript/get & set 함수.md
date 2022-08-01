# get & set 함수

클래스 내부에서 get과 set 함수를 이용해 값을 저장하고 불러올 수 있습니다.<br><br>

* get: 값을 불러온다.<br><br>

* set: 값을 저장한다.

```
class A {
    _name = 'no name';

    get name() {
        return this._name + '@@@';
    }

    set name(value) {
        this._name = value + '!!!';
    }
}

const a = new A(); //클래스 A의 객체 a생성
console.log(a);
a.name = 'Mark'; //set함수 호출:_name에 Mark저장
console.log(a);
console.log(a.name);
console.log(a._name);
```
<결과><br>
`A { _name: 'no name' }`
`A { _name: 'Mark!!!' }`
`Mark!!!@@@`
`Mark!!!`

## 출처
* 패스트캠퍼스 강의