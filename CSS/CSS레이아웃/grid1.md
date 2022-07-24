# grid-template-columns & grid=template-rows & gap(grid-gap)

## grid-template-columns
그리드 컨테이너의 트랙 중 열트랙에 있는 아이템들의 크기를 정해주는 속성입니다.<br>
트랙은 그리드 컨테이너의 행 또는 열을 뜻합니다.
```
 grid-template-columns: 100px 1fr;/*열 크기&개수를 지정한다.*/
 ```
(fr: 남아있는 공간에서 비율로 나눈다.)
<br>

## grid-template-rows
그리드 컨테이너의 트랙 중 열트랙에 있는 아이템들의 크기를 정해주는 속성입니다.
```
grid-template-rows: 200px 1fr 1fr;/*행 크기&개수를 지정한다.*/
```
<br>

## gap(grid-gap)
gap은 그리드 아이템의 간격 사이사이의 간격을 결정해주는 속성입니다.<br>
아래와 같이 단축속성으로도 작성가능합니다.
```
gap: 20px 10px;/*행사이의 간격은 20px, 열사이의 간격은 10px*/
```