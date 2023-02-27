# 이벤트 버블링 (Event Bubbling), 이벤트 캡쳐 (Event Capture), 이벤트 위임 (Event Delegation)

## 이벤트 버블링 (Event Bubbling)

#### : 특정 요소에서 이벤트가 발생했을 때, 해당 이벤트가 더 상위 요소로 전달되는 과정

브라우저는 특정 요소에서 이벤트가 발생했을 때 그 이벤트를 최상위에 있는 요소까지 전파한다.
이러한 과정을 이벤트 버블링이라고 부른다.

```
// html
<body>
	<div class="one">
		<div class="two">
			<div class="three">
			</div>
		</div>
	</div>
</body>

// js
var divs = document.querySelectorAll('div');
divs.forEach(function(div) {
	div.addEventListener('click', logEvent);
});

function logEvent(event) {
	console.log(event.currentTarget.className);
}
```

<결과>

```
three
two
one
```

## 이벤트 캡처 (Event Capture)

#### : 이벤트 버블링과 반대로 진행되는 이벤트 전달 과정

이벤트 캡처는 이벤트 버블링과 반대로 하위요소에서 상위요소로 이벤트 전달 과정이 진행된다.

```
// html
<body>
	<div class="one">
		<div class="two">
			<div class="three">
			</div>
		</div>
	</div>
</body>

// js
var divs = document.querySelectorAll('div');
divs.forEach(function(div) {
	div.addEventListener('click', logEvent, {
		capture: true // default 값은 false입니다.
	});
});

function logEvent(event) {
	console.log(event.currentTarget.className);
}
```

<결과>

```
one
two
three
```

`addEventListener`의 세번째 파라미터로 `capture: true`를 설정해주면
이벤트 캡처가 진행되어 가장 상위 요소에 적용된 이벤트가 먼저 발생한다.

### 이벤트 진행을 막고싶을 때는 어떻게 할까?

이벤트 버블링이나 이벤트 캡처를 구현할때 적용한 모든 요소에 이벤트를 실행하지 않고 중간에 멈추기 위한 속성이 있다.
`event.stopPropagation()`을 사용하면 이벤트의 진행과정을 중단시킬 수 있다.

```
// 이벤트 버블링 예제
divs.forEach(function(div) {
	div.addEventListener('click', logEvent);
});

function logEvent(event) {
	event.stopPropagation();
	console.log(event.currentTarget.className); // three
}

// 이벤트 캡쳐 예제
divs.forEach(function(div) {
	div.addEventListener('click', logEvent, {
		capture: true // default 값은 false입니다.
	});
});

function logEvent(event) {
	event.stopPropagation();
	console.log(event.currentTarget.className); // one
}
```

## 이벤트 위임 (Event Delegation)

#### : 하위 요소에 각각 이벤트를 붙이지 않고 상위 요소에서 하위 요소의 이벤트들을 제어하는 방식

```
// html
<h1>오늘의 할 일</h1>
<ul class="itemList">
	<li>
		<input type="checkbox" id="item1">
		<label for="item1">이벤트 버블링 학습</label>
	</li>
	<li>
		<input type="checkbox" id="item2">
		<label for="item2">이벤트 캡쳐 학습</label>
	</li>
</ul>

// js

// 새 리스트 아이템을 추가하는 코드
var itemList = document.querySelector('.itemList');

var li = document.createElement('li');
var input = document.createElement('input');
var label = document.createElement('label');
var labelText = document.createTextNode('이벤트 위임 학습');

input.setAttribute('type', 'checkbox');
input.setAttribute('id', 'item3');
label.setAttribute('for', 'item3');
label.appendChild(labelText);
li.appendChild(input);
li.appendChild(label);
itemList.appendChild(li);

var itemList = document.querySelector('.itemList');
itemList.addEventListener('click', function(event) {
	alert('clicked');
});
```

아이템이 새로 추가될 때마다 이벤트를 새로 추가하지 않고
상위 요소인 `.itemList`에 이벤트를 달아줌으로써 하위요소에도 이벤트가 등록되게 한다.

## 출처

- [캡틴 판교-이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)
