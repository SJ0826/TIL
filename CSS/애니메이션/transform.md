# transform :curly_loop:

: 대상이 되는 요소에 이동, 회전, 확대/축소, 비틀기 등의 변형 효과를 준다.

## transform의 속성값

<h3 style="background: lightgrey"> 1. translate(x, y) </h3>
: 요소의 좌표를 움직인다.

```css
transform: translate(20px, 25%);
```

대상 요소를 x축으로 20px만큼, y축으로 25%만큼 움직인다.

괄호안에 값이 하나만 입력된 경우, 두 영역에 동일한 값이 입력된 것으로 간주한다.

<h3 style="background: lightgrey"> 2. translateX(n) / translateY(n) </h3>

: 요소를 x축이나 y축 한방향으로 움직이고 싶을 때 사용한다.

```css
transform: translateX(20px);
```

<h3 style="background: lightgrey"> 2. scale(x, y) </h3>

: X축으로 x만큼, Y축으로 y만큼 요소를 축소 혹은 확대한다.

```css
transform: translateX(0.75, 1.1);
```

<h3 style="background: lightgrey"> 3. skewX(x) / skewY(y) </h3>

: 요소를 X, Y축으로 x도 만큼 또는 y도 만큼 기울인다.

```css
transform: skewX(15deg);
```

<h3 style="background: lightgrey"> 4. rotate(n) </h3>

: 요소를 n만큼 회전시킨다.

```css
transform: rotate(45deg);
```

---

## 출처

- [강력한 CSS](https://www.inflearn.com/course/%EA%B0%95%EB%A0%A5-css-%EC%BD%94%EB%93%9C%EC%BA%A0%ED%94%84/unit/135394)
