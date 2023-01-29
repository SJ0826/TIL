# animation

## animation 관련 속성

<h3 style="background: lightgrey"> 1. animation-name </h3>
: 어떤 keyframes를 요소에 적용할 것인지 지정
```css
animation-name: moveright;
```
<h3 style="background: lightgrey"> 2. animation-duration </h3>
: 애니메이션을 한 번 재생하는데 걸리는 시간을 설정
```css
animation-duration: 2s;
```
<h3 style="background: lightgrey"> 3. animation-direction </h3>
: 애니메이션의 재생 방향을 정의
```css
animation-direction: normal; // 기본값(정방향)
animation-direction: reverse; // 역방향
animation-direction: alternate; // 정방향으로 재생, 단 반복시 정방향/역방향을 번갈아 재생
animation-direction: alternate-reverse: 역방향으로 재생, 단 반복시 역방향/정방향을 번갈아 재생
```
<h3 style="background: lightgrey"> 4. animation-iteration-count </h3>
: 애니메이션 재생 횟수를 정의한다.

따로 지정하지 않으면 한번 재생되고 끝난다.

```css
animation-iteration-count: inifinite // 무한 반복;; ; ; ;
```

<h3 style="background: lightgrey"> 5. animation-timing-function </h3>
: 애니메이션 재생 패턴을 정의한다.

```css
animation-timing-function: ease-in-out;
```

<h3 style="background: lightgrey"> 6. animation-delay </h3>
: 애니메이션 시작을 얼마나 지연할 지 설정
```css
animation-delay : 2s
```

<h3 style="background: lightgrey"> animation 단축속성 순서 </h3>
```css
animation: moveRight(name) 0.4(duration) linear(timing-function) 1s(delay) infinite(iteration-count) alternate(direction)
```

---

## 출처

- [강력한 CSS](https://www.inflearn.com/course/%EA%B0%95%EB%A0%A5-css-%EC%BD%94%EB%93%9C%EC%BA%A0%ED%94%84)
