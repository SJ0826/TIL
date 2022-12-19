# Fetch
### : 원격 API를 호출할 수 있는 자바스크립트 내장 함수

## Fetch 사용법
Fetch함수는 두가지의 인자를 받는다.
1. URL
2. 옵션객체

인자를 받아 Promise객체를 반환한다.

반환된 객체는 API호출이 성공했을 때 응답(response) 객체를 **resolve**하고
실패했을 때는 예외(error)객체를 **reject**한다.
```
// fetch 예시
fetch(url, options) 
.then((response) => response.json()) // 네트워크에서 JSON파일을 가져와서 콘솔에 출력
.catch((error) => console.log("error:", error))
```
* `Response`: HTTP 응답 전체를 나타내는 객체. JSON 본문 콘텐츠를 추출하기 위해서는 `json()`메서드를 호출해야 한다. 

## GET 호출: 데이터 불러오기
fetch함수의 기본적인 동작은 `GET`이다.
```
fetch("https://jsonplaceholder.typicode.com/posts/1").then((response) =>
  console.log(response)
);

// 결과
Response {status: 200, ok: true, redirected: false, type: "cors", url: "https://jsonplaceholder.typicode.com/posts/1", …}
```
응답(response) 객체는 json메서드를 제공한다.

`json()`을 호출하면 응답 객체로부터 JSON 포멧의 응답을 자바스크립트 객체로 변환해서 얻을 수 있다.
```
// json()을 활용하여 응답객체를 자바스크립트 객체로 변환
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((data) => console.log(data));

// 결과
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit↵suscipit recusandae consequuntur …strum rerum est autem sunt rem eveniet architecto"
}
```

## POST 호출: 데이터 생성하기
POST는 원격 API에서 관리하고 있는 데이터를 생성할 때 사용한다.

* `method` 옵션을 `POST`로 지정한다.
* `headers`옵션을 통해 JSON포멧을 사용한다고 알려준다.
* 요청 전문을 JSON 포멧으로 직렬화하여 `body`옵션에 설정해준다. 
```
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "Test",
    body: "I am testing!",
    userId: 1,
  }),
}).then((response) => console.log(response));

// 결과: 응답코드가 201 Created
Response {type: "cors", url: "https://jsonplaceholder.typicode.com/posts", redirected: false, status: 201, ok: true, …}

// json메서드로 응답객체를 호출했을 때(response.json())
{title: "Test", body: "I am testing!", userId: 1, id: 101}
```

## PUT, DELETE 호출: 데이터 수정, 삭제하기
PUT과 DELETE는 데이터를 수정하거나 데이터를 삭제할 때 사용한다.

```
// PUT
fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "Test",
    body: "I am testing!",
    userId: 1,
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));

  // 결과
  {title: "Test", body: "I am testing!", userId: 1, id: 1}
  ```

  DELETE는 보낼 데이터가 없어 `header`와 `body`옵션이 필요없다.

  ```
  // DELETE
  fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "DELETE",
})
  .then((response) => response.json())
  .then((data) => console.log(data));

  // 결과
  {}
  ```

  ### fetch 함수 커스텀화 하기
  ```
  async function post(host, path, body, headers = {}) {
  const url = `https://${host}/${path}`;
  const options = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      ...headers,
    },
    body: JSON.stringify(body),
  };
  const res = await fetch(url, options);
  const data = await res.json();
  if (res.ok) {
    return data;
  } else {
    throw Error(data);
  }
}

post("jsonplaceholder.typicode.com", "posts", {
  title: "Test",
  body: "I am testing!",
  userId: 1,
})
  .then((data) => console.log(data))
  .catch((error) => console.log(error));
  ```

  ## 출처
  * [MDN-Fetch 사용하기](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch)
  * [DaleSeo-fetch()함수로 원격 API호출하기](https://www.daleseo.com/js-window-fetch/)
