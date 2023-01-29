# transition :on:

: CSS 속성을 이용한 변화의 전, 후 사이에 애니메이션을 추가해 움직임을 부드럽게 만들어주는 속성

## transition 속성

### 1. transition-property

: 어떠한 속성(property)에 transition을 적용할지 정한다.

```css
trasition-property: color, transform;
```

### 2. transition-duration

: transition에 걸리는 시간을 지정한다.

```css
transition-duration: 0.2s;
```

### 2. transition-timing-function

transition의 속도 패턴을 정한다.

```css
transition-duration: ease-in-out | linear | ease | ease-in | ease-out;
```

[CSS-Transition timing function sample](https://codepen.io/Joogumi/full/eYMgrKO)에서 각각의 속성들을 확인할 수 있다.

### 3. transition-delay

: transition 요청을 받은 후 실제로 실행되기까지 기다려야 하는 시간의 양을 지정

```css
transition-delay: 2s;
```

transition의 속성을 한번에 적어줄 수 있다.

```css
transition: color 0.4s (duration) ease-in-out(timing-function) 1s (delay);
```
