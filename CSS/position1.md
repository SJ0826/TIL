# position(relative & absolute)
position은 문서 상에 요소를 배치하는 방법을 정의합니다.<br>

## position의 속성값
1. **static**: 기본값
2. **relative**: 일반적인 문서의 흐름에 따라 배치하되, 상하좌우 위치 값에 따라 오프셋을 적용합니다.
```
div{
    width: 100px; height: 100px;
    background-color: red;

    position: relative;
    top: 100px; left: 100px;
}
```
> 원래 위치보다 위에서부터 100px, 왼쪽에서부터 100px 떨어진다.
<br>
<br>

3. **absolute**: 요소를 일반적인 문서의 흐름에서 제거하고,<br>
상위 요소 중 가장 가까운 position지정 요소에 대해 상대적으로 오프셋을 적용합니다.
```
div{
    width: 100px; height: 100px;
    background-color: red;

    position: relative;
    top: 100px; left: 100px;
}
```
만약, 상위요소에 position을 지정하고 있는 요소가 없다면 <br>
absolute는 브라우저 화면을 기준으로 위치를 지정합니다.