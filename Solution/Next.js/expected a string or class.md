# expected a string or class/function

## 에러 발생

```
Unhandled Runtime Error
Error: Element type is invalid: expected a string (for built-in components) or a class/function (for composite components) but got: undefined. You likely forgot to export your component from the file it's defined in, or you might have mixed up default and named imports.

Check the render method of `Home`.
```

## 원인

`Link`를 import해오는 과정에서 중괄호를 썼다.

```
import { Link } from 'next/link'
```

## 해결

중괄호를 없애줬다.

```
import Link from 'next/link'
```
