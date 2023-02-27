# Redux-Persist

![Redux-Persist](https://images.velog.io/images/_jouz_ryul/post/2da7cd90-728f-45bb-8459-20a49d96dc83/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-05-24%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%201.53.11.png)

모코숲 프로젝트를 진행하는 중 새로고침하면 리덕스 store에 저장되어 있던 데이터들이 reset되었다.

페이지가 처음 로딩될 때 api를 매번 요청할 수는 있지만, 더 효율적인 방법이 있을까 고민하던 중 Redux-Persist라는 라이브러리를 알게 되었다.

## Redux-Persist

Redux-Persist는 state를 **Local Storage** 혹은 **Session Storage**에 저장해 새로고침을 해도 state를 유지시키는 redux 라이브러리이다.

## 사용방법

#### 1. 설치 (yarn + typescript 환경)

```
yarn add redux-persist @types/redux-persist
```

#### 2. Storage 종류에 따라 `import`

- Local Storage를 사용할 경우

```
import storage from 'redux-persist/lib/storage
```

- Session Storage를 사용할 경우

```
import sessionStorage from 'redux-persist/lib/storage
```

이 과정에서 발생한 에러로 redux-persist를 몇번이나 재설치했다.

🔗 [TIL-Could not find a declaration file of module](https://github.com/SJ0826/TIL/tree/main/React/TroubleShooting)

에러는 TIL폴더에 정리해 두었다.

#### 3. config 작성 후, rootReducer를 감싼다.

```ts
// store/index.ts

const persistConfig = {
  // config 작성
  key: "root",
  storage,
  whiteList: ["studyItem", "member", "studyList"], // 적용할 리듀서를 whiteList에 포함시킨다.
};

const rootReducer = combineReducers({
  userForm: userFormSlice,
  signInForm: signInFormSlice,
  member: memberSlice,
  editMode: editModeSlice,
  userMenu: userMenuSlice,
  studyForm: studyFormSlice,
  studyList: studyListSlice,
  studyItem: studyItemSlice,
});

const persistedReducer = persistReducer(persistConfig, rootReducer);

const store = configureStore({
  reducer: persistedReducer,
  middleware: (getDefaultMiddleware) =>
    getDefaultMiddleware({ serializableCheck: false }).concat(logger),
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
export default store;
export const persistor = persistStore(store); // 작성된 persistor은 index.tsx에서 사용된다.
```

#### 4. index.tsx파일에 적용시키기

```ts
// index.tsx

const root = ReactDOM.createRoot(
  document.getElementById("root") as HTMLElement
);
root.render(
  <Provider store={store}>
    <PersistGate loading={null} persistor={persistor}>
      <ThemeProvider theme={theme}>
        <GlobalStyle />
        <Page>
          <App />
        </Page>
      </ThemeProvider>
    </PersistGate>
  </Provider>
);
```

#### 5. 결과

이렇게 모든 과정을 거치면
![image](https://user-images.githubusercontent.com/56298540/221575158-e2ecd4ad-3fd7-4ca3-9211-89c96a48ba77.png)

localStorage에 persist:root라는 이름의 키로 값이 저장된 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/56298540/221575667-eceb31b1-4458-43e3-9d4d-820a86b9c201.png)

logger에도 반영되어 console창에서도 확인할 수 있다.

REHYDRATE과정에서 storage에 저장된 값을 가져와 state로 설정해 준다.

## storage에 있는 데이터 삭제하기

브라우저를 완전히 떠났을 때 데이터가 남아있으면 안되므로 로그아웃시 locas Storage에 저장된 state들을 삭제해 주었다.

```ts
const onClickLogout = async () => {
  await persistor.purge();
  navigator("/signin");
  removeToken();
};
```

---

redux-persist를 사용하니 모든 페이지별 api요청 수가 줄었다.

하지만 storage가 너무 무거워질 수 있으니, 정말 필요하거나 모든 페이지에서 사용되는 state정도만 저장하는 편이 좋을 듯 하다.

또한 중요한 정보가 담겨있는 state는 persist사용을 자제하는 편이 좋겠다.

## 참조

- [GROWNFRESH-Redux-Persist](https://grownfresh.tistory.com/191)
