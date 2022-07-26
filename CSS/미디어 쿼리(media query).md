# 미디어 쿼리(media query)
미디어 쿼리는 미디어 타입을 인식하고, <br>
콘텐츠를 읽어들이는 기기나 브라우저의 물리적 속성을 감지할 수 있는 기능입니다.<br><br>

* @media: 미디어 쿼리문 선언<br><br>

* screen: 가장 자주 사용되는 미디어 타입 중 하나. 화면을 뜻합니다.

```
 /*미디어 쿼리문*/
        @media screen and (min-width: 800px){/*800px 보다 화면이 커졌을 경우에 적용한다.*/
            img{
                width: 400px;
                height: 400px;
            }

        }
```

## 미디어 쿼리 적용의 다른 형태
### link 태그에 미디어 쿼리 추가
```
<link rel="stylesheet" href="style.css"
media="screen and (max-width: 768px)">
```

### @import 구문을 이용한 추가
```
@import url("style.css") screen and max-width: 768px);
```

## 참조
* 유노코딩 초보자를 위한 반응형 웹 기초 강의