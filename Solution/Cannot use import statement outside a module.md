# Cannot use import statement outside a module

## 에러 발생

공연 검색기 프로젝트 중 에러가 발생했다.
![image](https://user-images.githubusercontent.com/56298540/204087683-584215fd-951e-4b24-af3a-1d91c588a46d.png)

## 에러 원인

해당 스크립트를 모듈로 인식하지 못해 `import`문을 쓸 수 없다는 뜻이다.

직접 스크립트의 타입을 지정해주어야 한다.

## 에러 해결

```
// index.html

    <script src="main.js" type="module"></script>
```

이렇게 해당 스크립트 태그에서 타입을 모듈로 지정해주면 에러가 해결된다.
