# CSS 텍스트 꾸미기

## font-family
글꼴을 정의합니다.<br>
여러 개의 글꼴을 연달아 작성하여 우선순위를 정할 수 있습니다.
```
p{
    font-family: Times.monospace, serif;
}
```
<br>

## font-size
글자 크기를 정의합니다.
<br>

* px: 모니터 상의 화소 하나 크기에 대응하는 절대적인 크기
```
span{ font-size: 16px; }
```
* rem: <html> 태그의 font-size에 대응하는 상대적인 크기
```
span{ font-size: 2rem; }
```
* em: 부모태그(상위태그)의 font-size에 대응하는 상대적인 크기
```
span{ font-size: 1.5em; }
```
<br>

## text-align
정렬 방식 정의한다.
* left/right: 왼쪽 또는 오른쪽 정렬한다.<br>
* center: 가운데 정렬한다.<br>
* justify: 양끝 정렬한다.(마지막 줄 제외)<br>
```
p{ text-align: right; }
```
<br>

## color
글자 색상을 정의합니다.
* 키워드: 미리 정의된 색상별 키워드를 정의합니다. <br>
* RGB 색상 코드: # + 여섯자리 16진수 값 형태로 지정합니다. <br>
* RGB 함수: Red, Green, Blue의 수준을 각각 정의해 지정합니다.<br>
```
span{ color: red; }
span{ color: #FF000; }
span{ color: rgb(100%, 0%, 0%); }
```