# Type '{...}' has no properties in common with type 'IntrinsicAttributes'

## 에러 발생

프로젝트 과정 중 `_app.tsx`파일에서 에러가 발생했다.

```
Type '{...}' has no properties in common with type 'IntrinsicAttributes'
```

![image](https://user-images.githubusercontent.com/56298540/199910984-f7921555-15c3-4a4c-b25a-52709ee859d2.png)

## 에러 원인

해당 컴포넌트의 props인 children이 존재하지 않는다는 뜻이다.

## 에러 해결

props를 설정해서 타입을 지정해주자.

```
import React from 'react'

interface Props {
  children?: React.ReactNode
  [k: string]: any
}

export default function Layout({ children, ...props }: Props) {
  return <div>Layout</div>
}
```

Props를 interface로 설정해서 타입을 지정하고 컴포넌트에 설정해 주었다.
