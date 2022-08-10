# CSSO

## CSSOM이란?

CSSOM은 CSS Object Model의 약자입니다.<br><br>

브라우저에서 dom을 만들게 되면, css을 병합해서 cssom을 만듭니다.<br><br>

CSSOM에서 CSS에는 cascading이라는 규칙이 존재하기 때문에 따로 CSS를 정의하지 않아도 브라우저에서 설정된 기본적인 CSS파일이 있다면 그것들이 전부 다 적용됩니다.<br><br>

dom과 cssom을 합해서 최종적으로 rendertree를 만듭니다.<br><br>

rendertree에는 사용자에게 궁극적으로 보여지는 요소만 선별됩니다.<br><br>

```
opacity: 0;
visibility: hidden;
```

> Render Tree에 포함됨.

```
display: none;
```

> Render Tree에 포함되지 않음.

## 출처

- 드림코딩
