# display속성&border속성

## 1. display 속성
display 속성은 요소를 블록과 인라인 요소 중 어느 쪽으로 처리할지 정의합니다.<br>
<br>

### display 속성 값
* inline: 인라인으로 처리<br><br>
* block: 블록 레벨로 처리<br><br>
* inline-block: 인라인으로 배치하되, 블록 레벨 요소의 속성을 추가할 수 있도록 처리<br><br>
* none: 존재는 하되, 디스플레이하지 않음

```
div{ display: inline; }
div{ display: block; }
div{ display: inline-block; }
div{ display: none; }
```

## border 속성
요소가 차지하고 있는 영역에 테두리를 그릴 수 있습니다.<br>
border 속성에는 속성값으로 테두리의 두께, 모양, 크기 등을 함께 지정할 수 있는데,<br>
이러한 속성을 '단축속성'이라고 합니다.
```
<!--두꼐가 2px인 직선 모양(solid)의 초록(green) 테두리를 만들어줘-->
span{ border: 2px solid green; }
```
<br>

### border 속성의 하위 속성
* border-color: color 정의 방식과 동일<br><br>
* border-width: thin, medium, thick 등의 키워드 또는 px, em, rem 등의 단위<br><br>
* border-style: none, solid, dotted, dashed 등<br><br>