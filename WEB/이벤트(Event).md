# Event(이벤트)

## Event란?

- 프로그래밍 하고 있는 시스템에서 일어나는 사건.<br><br>

- 이벤트에 대한 반응을 코드로 작성시켜 이벤트가 발생되었을 때 자동적으로 상호작용이 가능하도록 한다.<br><br>

## Event Handler(이벤트 핸들러)란?

- 특정한 이벤트가 발생했을 때, 실행되는 코드 블럭<br><br>

- Event Handler를 등록할 수 있는 모든 요소는 Node를 상속하고, Node는 Event Target을 상속하므로 모든 Element는 Event Target이다.<br>
  따라서 **모든 Element는 Event Target**이다.<br>

* > Event Target이란? Event가 등록되어 있는 요소

* ![이벤트 필기](https://user-images.githubusercontent.com/56298540/184467880-92a2ad69-bac9-44db-aafe-1d9ef432c5b2.jpg)

* Event Handler는 Event Listner라고 부르기도 한다.

## Event 발생 과정

1. 특정한 요소에 Event Handler를 등록한다.

2. 나중에 사용자가 이벤트를 발생시키면, 브라우저는 Event Object를 만들어서 등록한 callback 함수에 전달한다.

## Event Target의 API

이벤트 타겟에서는 세개의 API가 있다.<br>

1. EventTarget.addEventListener(): 이벤트 타겟에 특정한 이벤트 핸들러를 등록.

2. EventTarget.removeEventListener(): 이벤트 타겟으로부터 특정한 이젠트 리스너를 지움

3. EventTarget.dispatchEvent(): 이벤트 타겟에 인공적으로 이벤트를 발생시킴.

## Capturing(캡쳐링)과 Bubbling(버블링)

### Capturing

Element들이 부모와 자식노드들이 경우, 브라우저는 캡쳐링을 거친다.<br><br>
부모 컨테이너에서부터 시작해서 자식 컨테이너까지 캡쳐링을 통해 내려오고 자식 컨테이너에 등록된 Event Handler를 호출한다.<br><br>

대부분 엔지니어들이 캡쳐링 단계에서 무언가를 처리하는 것은 거의 없다.<br><br>

### Bubbling

버블링은 **상위의 부모에게 등록된 이벤트를 호출**하는 것이다.<br><br>

엔지니어가 호출하는 것이 아니라 브라우저에서 자동적으로 실행된다.<br><br>

버블링을 멈추고 싶다면 `stopPropagation()`을 사용하고, 하나의 엘리먼트에 함께 등록된 이벤트도 무시하고 싶다면 `stopImmediatePrpagation()`을 사용한다.<br><br>

하지만 **사용하지 않는 것이 좋다.**<br><br>

다른 엔지니어를 고려하지 않고 이벤트를 무시하게 되면 예상치 못한 오류가 발생할 확률이 크다.<br><br>

대신에 `event.target`과 `event.currnetTart`가 같지 않은 경우 `return`을 함으로써 필요하지 않은 이벤트를 무시한다.

```
if (event.target !== event.currentTarget) {
  return;
}
```

## 출처

- 드림코딩

- [MDN](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Building_blocks/Events)
