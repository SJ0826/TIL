# flex-basis & flex

## flex-basis(기본값 : auto)
플렉스 아이템의 초기 크기를 지정합니다.<br>
box-sizin이 따로 설정되지 않은 경우, 콘텐츠 박스의 크기를 결정합니다.<br>

```
li:nth-child(2){ /*플렉스 컨테이너가 처음 만들어졌을 때 기본 크기를 정해줌.*/
    flex-basis: 100px; /*두번째 아이템 기본 크기: 100px*/
    flex-shrink: 2;
}
```

## flex
flex-grow, flex-shrink, flex-basis의 세 가지 속성을 한번에 정의할 수 있는 단축 속성입니다.

```
.item{
    flex: 0 0 200px;/* 200px보다 크거나 작을 수 없음*/
    flex: 0 1 200px;/*늘어나진 않지만 줄어들 수는 있음.*/
}
```