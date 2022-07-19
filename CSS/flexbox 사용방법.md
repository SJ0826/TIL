# flexbox 사용방법
flexbox란 박스 내 요소 간의 공간 배분과 정렬 기능을 제공하기 위한1차원 레이아웃 모델입니다.<br><br>
레이아웃을 다룰 때 한 번에 하나의 차원(행이나 열)만을 다루는 특성을 가지고 있습니다.<br><br>
flexbox에는 주축(main-axis)과 교차축(cross-axis)이 있습니다.

## flexbox의 속성값
* **row**: 기본값. 주축은 행이고 방향은 콘텐츠 방향과 동일<br>
* **row-reverse**: 주축은 행이고 방향은 콘텐츠 방향과 반대<br>
* **column**: 주축은 열이고 방향은 콘텐츠의 방향과 동일<br>
* **column-reverse**: 주축은 열이고 방향은 콘텐츠의 방향과 반대<br>
```
 <style>
    .container{ 
        display: flex;/*flex컨테이너는 기본적으로 행방향을 가지고 있음*/
        flex-direction: row-reverse;/*진행은 행으로 하지만 방향이 반대*/
    } 
    .item{
        width: 80px; height: 80px;
        background-color: orange;
    }
</style>
```
flexbox를 flex 컨테이너라고 부르기도 합니다.