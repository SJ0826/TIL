# 스택(Stack)

![스택](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Data_stack.svg/300px-Data_stack.svg.png)

스택은 가장 먼저 들어온 데이터가 가장 먼저 나중에 나가는 구조 입니다.

코드를 작성할 때 많이 사용하는 `Ctrl + z`를 떠올리면 이해하기 쉽습니다.

## 스택 구현해보기

자바스크립트로 연결리스트를 이용해 스택을 구현합니다.

```js
import { LinkedList } from "./LinkedList.mjs";

class Stack {
  constructor() {
    this.list = new LinkedList();
  }

  push(data) {
    this.list.insertAt(0, data);
  }

  pop() {
    try {
      return this.list.deleteAt(0);
    } catch (e) {
      return null;
    }
  }

  peek() {
    return this.list.getNodeAt(0);
  }

  isEmpty() {
    return this.list.count == 0;
  }
}

export { Stack };
```
