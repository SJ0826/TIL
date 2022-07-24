# grid-column & row

그리드 컨테이너의 줄번호를 이용하여 아이템을 배치하고 크기를 지정합니다.<br>

```
grid-row: 1 / 2;  /*1번 아이템이 행의 1~2번까지 크기를 차지한다.*/
grid-column: 1 / 3; /*1번 아이템이 열의 1~3번까지 크기를 차지한다.*/
```


<br>
<br>
다른 방식으로도 크기를 지정할 수 있습니다.

```
grid-row-start: 1; /* 행의 1번줄부터 3번줄까지 크기 차지*/
grid-row-end: 3;
grid-column-start: 2;/* 열의 2번줄부터 4번줄까지 크기 차지*/
grid-column-end: 4;
```