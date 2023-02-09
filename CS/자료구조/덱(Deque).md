# 덱(Deque)

![덱](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F9955354C5C4723F11C)

덱(Deque)은 데이터의 삽입과 제거를 **head**와 **tail** 두 곳에서 자유롭게 할 수 있는 자료구조입니다.

## 덱의 추상자료형

- `printAll` - 모든 데이터 출력
- `addFirst` - head에서 데이터 제거
- `removeFirst` - head에서 데이터 제거
- `addLast` - tail에 데이터 삽입
- `removeLast` - tail엣 데이터 제거
- `isEmpty` - 리스트가 비었는지 체크

## 자바스크립트로 구현해보기

```js
import { DoublyLinkedList } from "./DoublyLinkedList.mjs";

class Deque {
  constructor() {
    this.list = new DoublyLinkedList();
  }

  printAll() {
    this.list.printAll();
  }

  addFirst(data) {
    this.list.insertAt(0, data);
  }

  removeFirst() {
    return this.list.deleteAt(0);
  }

  addLast(data) {
    this.list.insertAt(this.list.count, data);
  }

  removeLast() {
    return this.list.deleteLast();
  }

  isEmpty() {
    return this.list.count == 0;
  }
}

export { Deque };
```

## 출처

- [그림으로 배우는 자료구조와 알고리즘](https://www.inflearn.com/course/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B8%B0%EB%B3%B8)
