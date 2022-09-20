# tsc: 이 시스템에서 스크립트를 실행할 수 없으므로...

![image](https://user-images.githubusercontent.com/56298540/191191465-b2232cde-4eb2-446b-bc98-5c8632683be8.png)

```
C:\Users\ikosd_000\Desktop\practice\learn-typescript\getting-started> tsc index.ts
tsc : 이 시스템에서 스크립트를 실행할 수 없으므로 C:\Users\ikosd_000\AppData\Roaming\npm\tsc.ps1 파일을 로드 tsc : 이 시스템에서 스크립트를 실행할 수 없으므로 C:\Users\ikosd_000\AppData\Roaming\npm\tsc.ps1 파일을 로드
```

`tsc`명령어를 이용해서 `ts`파일을 `js`파일로 변환하는 작업을 하려고 하는데 터미널에서 에러가 났다.

## 해결방법

1. Visual Studio Code 관리자 권한으로 실행
2. terminal에 순서대로 입력

```
$ Get-ExecutionPolicy
```

```
$ Set-ExecutionPolicy RemoteSigned
```

`Restricted`에서 `RemoteSigned`로 변경했다.

- `Restrcted`: (제한된) 기본 실행 정책, 명령어 하나씩 실행 가능, 스크립트 파일을 로드하여 실행할 수 없음.
- `RomotedSigned`: 로컬 컴퓨터에서 본인이 생성한 스크립트만 실행 가능, 인터넷에서 다운로드한 스크립트는 신뢰된 배포자에 의해 서명된 것만 실행할 수 있음.

## 출처

[꿀벌 코딩](https://cobee.tistory.com/entry/TypeScript%EC%98%A4%EB%A5%98-tsc-%EC%9D%B4-%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%97%90%EC%84%9C-%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%A0-%EC%88%98-%EC%97%86%EC%9C%BC%EB%AF%80%EB%A1%9C-%EB%B3%B4%EC%95%88-%EC%98%A4%EB%A5%98)
