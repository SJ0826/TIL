# flexbox 관련 속성
flexbox를 다루기 위한 다양한 속성들이 있습니다.<br><br>

* **justyfy-content**: 주축에서의 요소 배치 방법을 정의합니다.<br><br>
* **align-items**: 교차축에서의 요소 배치 방법을 정의합니다.<br><br>
* **align-flexbox**: 개별 요소의 교차축 배치 방법을 정의합니다.<br><br>
* **flex-wrap**: 개별 요소들의 도합 크기가 컨테이너 주축 길이보다 커졌을 때의 처리 방법 및 방향을 정의합니다.<br><br>
```
 <style>
    .container{
        display: flex;
        width: 300px; height: 300px;
        border: 2px solid black;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;/*주축요소들의 합이 flex컨테이너의 크기보다 커졌을때, 두행 이상으로 처리함*/
    }
    .item{
        width: 120px; height: 60px; 
        /*flex컨테이너의 자식요소가 flex컨테이너보다 크기가 크면, flex컨테이너는 자식요소를 자동 수축시킴.*/
        background-color: teal;
    }
    /*.self{
        align-self: flex-start;개별요소 하나하나에 지정해서 요소를 배치시키는 속성
    } */
</style>
```