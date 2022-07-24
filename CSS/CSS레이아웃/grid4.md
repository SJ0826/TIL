# align & justify

## align-items
그리드 컨테이너 행 트랙의 높이안에서의 그리드 아이템의 배치를 결정합니다.<br>
그리드 컨테이너에 지정합니다.<br>

```
align-items: stretch;/*기본값: 행의 높이만큼 늘어난다.*/
align-items: start;/*행의 시작부분에 붙는다.*/
align-items: end;/*행의 끝에 붙는다.*/
```

## align-self
각각의 그리드 아이템이 어떤 식으로 배치될 것인지를 스스로 결정합니다.<br>

```
li:nth-child(2){ align-self: start;} /*2번 아이템에만 start적용*/
```

## justify-items
그리드 컨테이너 열 너비안에서의 그리드 아이템의 배치를 결정합니다.<br>
즉, align-items와 교차되는 속성입니다.<br>
그리드 컨테이너에 지정합니다.<br>

```
justify-items: stretch;
justify-items: start;/*열너비의 시작부분에 붙는다.*/
justify-items: end;/*열너비의 끝에 붙는다.*/
```

## justify-self
수평축(행)을 따라 각각의 그리드 아이템이 어떤 식으로 배치될 것인지를 스스로 결정합니다.<br>

```
li:nth-child(3){ justify-items: end;}/*3q번 아이템에만 end적용*/
```