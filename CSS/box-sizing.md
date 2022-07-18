# box-sizing

## 1. box-sizing 속성
box-sizing 속성은 너비와 높이가 포함할 영역을 변경함으로써<br>
너비와 높이의 계산 방법을 결정할 수 있습니다.<br><br>
* **content-box**: 기본값. 너비와 높이가 콘텐츠 영역만을 포함합니다. padding이 추가 되어도 content크기는 보장받고 싶을 때 씁니다.<br><br>
* **border-box**: 너비와 높이가 안쪽 여백과 테두리까지 포함합니다.
```
div{
    content-box: border-box;
}
```
border-box도 위와 같이 지정합니다.
![box-sizing](https://user-images.githubusercontent.com/56298540/179513956-1f50d8e2-0e09-402c-93f9-74b6366a26a3.png)

개발자도구를 통해<br>
padding이 추가되어도 content크기는 변하지 않은 것을 확인할 수 있습니다.