# 윈도우 스크롤링

## Window.scroll()

`window.scroll()` 함수는 윈도우의 원하는 위치로 스크롤하게 해주는 API입니다.<br><br>

### 사용방법

#### scroll(x좌표, y좌표)

첫번째 방법은 파라미터값을 받아오는 방법입니다.<br>

```
<button onclick="scroll(0,100);"></button>
```

> 창 상단에 수직 100번째 픽셀을 배치한다.

#### OPTION들

```
window.scroll({
  top: 100,
  left: 100,
  behavior: 'smooth'
});
```

- `top`: Y축을 따라 픽셀 수를 지정
- `left`: X축을 따라 픽셀 수를 지정
- `behavior`: `smooth`를 지정하면 스크롤이 부드럽게 애니메이션 된다.

## Window.scrollBy()

주어진 값만큼 윈도우에서 스크롤링하는 함수입니다.<br>

### 사용방법

사용방법은 window.scrollBy()와 크게 다르지 않습니다.<br><br>

#### scrollby(x축 방향 크기, y축 방향 크기)

첫번째 방법은 파라미터값을 받아오는 방법입니다.<br>

```
window.scrollBy(0, window.innerHeight); // 페이지 아래로 스크롤 할때
window.scrollBy(0, -window.innerHeight); // 페이비 위로 스크롤 할때
```

> 창 상단에 수직 100번째 픽셀을 배치한다.

#### OPTION들

```
window.scroll({
  top: 100,
  left: 100,
  behavior: 'smooth'
});
```

- `top`: Y축을 따라 픽셀 수를 지정
- `left`: X축을 따라 픽셀 수를 지정
- `behavior`: `smooth`를 지정하면 스크롤이 부드럽게 애니메이션 되고, `instant`를 지정하면 즉시 해당 위치로 점프하게 됩니다.
