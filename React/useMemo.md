# useMemo
```
import { useMemo } from 'react';

const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```
`useMemo`는 이전에 연산된 값을 재사용한다.

첫 번째 인자로 콜백 함수를, 두 번째 인자로 의존성 배열을 받는다.

두 번째 인자인 배열의 요소 값이 업데이트될 때만 콜백 함수를 다시 호출한다.

만약 빈 배열을 넘겨주면 맨 처음 컴포넌트가 마운트 되었을 때만 값을 계산하고 이후에는 `memoizaton`된 값ㅇ을 꺼내서 사용한다.

원하는 값이 바뀌지 않으면 리렌더링할 때 이전의 값을 재사용한다.

성능을 최적화해야하는 상황에서 사용한다.

## 주의할 점
`useMemo`는 꼭 필요한 경우에만 사용한다. 

값을 재활용하기 위해 따로 메모리에 값을 저장해 놓기 때문이다.

불필요한 값을 저장하면 성능이 안좋아질 수 있다.

## 출처
- [코딩병원](https://itprogramming119.tistory.com/entry/React-useMemo-%EC%82%AC%EC%9A%A9%EB%B2%95-%EB%B0%8F-%EC%98%88%EC%A0%9C)

* 패스트캠퍼스 for velopert
    