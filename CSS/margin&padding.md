# margin $ padding 다루기
박스모델의 여백은 상하좌우 네 개의 면에 존재하는 여백입니다.<br>

## 1. 하위 속성 정의하기
```
div{
padding-top: 10px;
padding-right: 20px;
padding-bottom: 30px;
padding-lefr: 40px;
}
```
위와 같이 margin에도 동일한 접미사를 붙여 개별 정의할 수 있습니다.<br><br>

## 2. 여러 값을 한 번에 정의하기
```
span{
    display: inline-block;
    width: 100px; height: 100px;
    margin: 10px 20px 30px 40px;
    <!--순서: top-right-bottom-left-->
}
```
위와 같이 padding에도 동일한 접미사를 붙여 개별 정의할 수 있습니다.<br><br>

