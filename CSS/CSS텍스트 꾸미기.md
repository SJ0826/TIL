# CSS 텍스트 꾸미기

## font-family

글꼴을 정의한다.<br>
여러 개의 글꼴을 연달아 작성하여 우선순위를 정할 수 있다.

```css
p {
  font-family: Times.monospace, serif;
}
```

<br>

## font-size

글자 크기를 정의한다.
<br>

- px: 모니터 상의 화소 하나 크기에 대응하는 절대적인 크기

```css
span {
  font-size: 16px;
}
```

- rem: <html> 태그의 font-size에 대응하는 상대적인 크기

```css
span {
  font-size: 2rem;
}
```

- em: 부모태그(상위태그)의 font-size에 대응하는 상대적인 크기

```css
span {
  font-size: 1.5em;
}
```

<br>

## text-align

정렬 방식 정의한다.

- left/right: 왼쪽 또는 오른쪽 정렬한다.<br>
- center: 가운데 정렬한다.<br>
- justify: 양끝 정렬한다.(마지막 줄 제외)<br>

```css
p {
  text-align: right;
}
```

<br>

## color

글자 색상을 정의한다.

- 키워드: 미리 정의된 색상별 키워드를 정의한다. <br>
- RGB 색상 코드: # + 여섯자리 16진수 값 형태로 지정한다. <br>
- RGB 함수: Red, Green, Blue의 수준을 각각 정의해 지정한다.<br>

```css
span {
  color: red;
}
span {
  color: #FF000;
}
span {
  color: rgb(100%, 0%, 0%);
}
```

## line-height

글자가 위치한 높이의 크기(행간)를 의미한다.

단위를 입력하지 않으면 브라우저가 자동으로 배율로 인식한다.

```css
line-height: 52px;
```

## letter-spacing

텍스트의 자간을 설정한다.

해당 수치만큼 자간이 가까워진다.

```css
letter-spacing: 20px;
letter-spacing: -2px;
```

## word-spacing

띄어쓰기를 기준으로한 단어의 간격을 의미한다.

```css
word-spacing: 20px;
```

## text-indent

텍스트의 들여쓰기를 결정한다.

```css
text-indent: 50px;
```

## text-transform

영문 텍스트의 대/소문자를 바꿀 수 있다.

```css
text-transform: none;
text-transform: capitalize;
text-transform: uppercase;
text-transform: lowercase;
```

## overflow

콘텐츠가 커서 요소 안에서 내용을 다 보여주기 힘들 때, 어떤 방식으로 보여줄지 결정한다.

```css
overflow: visible(기본값);
overflow: hidden;
overflow: scroll; // 무조건 스크롤 적용
overflow: auto; // 콘텐츠 밖으로 텍스트가 넘쳤을때만 스크롤 적용
```

## text-overflow

텍스트가 한줄일 때, 요소 밖으로 넘치는 text를 어떻게 표기할지 결정한다.

**선행 조건**

1. `white-space: nowrap;`
2. `overflow: hidden;`

```css
text-overflow: clip(기본값); // 공간에 맞게 텍스트가 잘림
text-overflow: ellipsis; // 잘린 텍스트를 말줄임표를 이용해 표현
```

---

## 출처

- [강력한 CSS](https://www.inflearn.com/course/%EA%B0%95%EB%A0%A5-css-%EC%BD%94%EB%93%9C%EC%BA%A0%ED%94%84)
