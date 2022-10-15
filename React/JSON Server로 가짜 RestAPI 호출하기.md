# JSON Server로 가짜 RestAPI 호출하기

프론트 작업을 할때 매번 백엔드를 개발해서 RestAPI를 호출하기 보다는

JSON Server를 사용하면 손쉽게 연습용 RestAPI를 호출할 수 있다.

## JSON 서버 만들기
### 1. data.json 폴더 만들기
폴더 안에 사용할 데이터를 작성한다.

<예시>
```
{
  "posts": [
    {
      "id": 1,
      "title": "리덕스 미들웨어를 배워봅시다",
      "body": "리덕스 미들웨어를 직접 만들어보면 이해하기 쉽죠."
    },
    {
      "id": 2,
      "title": "redux-thunk를 사용해봅시다",
      "body": "redux-thunk를 사용해서 비동기 작업을 처리해봅시다!"
    },
    {
      "id": 3,
      "title": "redux-saga도 사용해봅시다",
      "body": "나중엔 redux-saga를 사용해서 비동기 작업을 처리하는 방법도 배워볼 거예요."
    }
  ]
}
```

### 2. 작성한 파일을 기반으로 서버를 연다.

`$ npx json-server ./data.json --port 4000`

이렇게 터미널에 입력하면
가짜 `API` 서버가 `4000` 포트로 열린다.

### 3. axios를 사용하여 API 요청하기
프로젝트에 REST API Client인 `axios`를 설치한다.

`$ yarn add axios`

만들어진 서버를 `axios`를 사용하여 호출해서 데이터를 받아온다.

```
// post.js
import axios from 'axios';

// 포스트 목록을 가져오는 비동기 함수
export const getPosts = async () => {
  const response = await axios.get('http://localhost:4000/posts');
  return response.data;
};
```

## 출처
* 패스트캠퍼스 for velopert
    
