# 개발자의 기본기 :sailboat:

원티드 프론트엔드 인턴십 오티 이후 처음으로 진행한 강의를 들었다.

그동안 혼자 프로젝트를 하거나 강의를 들으면서 prettier나 esLint를 썼지만 이 포맷팅 툴은 혼자쓸 때보다 협업을 하는 과정에서 더 중요하다고 배웠다.

함께 진행하는 프로젝트에서 문법이나 코드 규칙이 서로 엇갈린다면 통일성이 떨어져 비효율을 유발하기 때문이다.

이번 강의에서는 코드를 가지고 다른 개발자들과 소통할 수 있는 방법들을 배웠다.

### 1. 커밋 메시지 규칙을 정해서 작성하자

공부하면서 여러 커밋 메시지 컨벤션을 찾아봤다.

똑같이 기능 추가를 뜻하지만 어떤 곳은 `Add` 어떤 곳은 `Feat`을 쓴다.

각자 쓰던 방식이 있겠지만 소통을 위해 규칙을 정하는 편이 좋다.

메시지 내용 또한 "작업중", "커밋" 등 간단하게 작성하는 것은 지양한다.

본인이 작업한 내용을 올바르게 작성하는 편이 좋다.

### 2. History를 관리하자

내가 작업하던 방식은 커밋을 다 하고 작업을 마무리 하기 전에 한번에 push했다.

하지만 중간에 노트북이나 컴퓨터가 가동이 안되는 상황이 온다면 작업한 내용을 한번에 날리게 되어 push도 그때그때 하는 것이 바람직하다고 배웠다.

History를 관리하는 규칙은 다음과 같다.

1. 커밋은 원하는 만큼 최대한 많은 시점에 한다.
2. 그때그때 push한다.
3. 최종적으로 브랜치의 작업이 마무리되고 PR을 통해 master에 머지 요청을 하기 전에 적절하게 커밋을 정리한다.

- 참고자료
  https://www.delftstack.com/ko/howto/git/git-squash-commits/

### 3. ESLint와 Prettier, 그리고 Husky

##### ESLint: 일관되고 버그를 피할수 있는 코드를 짜기위해서 만들어진 코드 분석 툴

- 설치: `npm install eslint --save-dev`
- CRA한 프로젝트에는 내장되어 있어 따로 설치할 필요가 없음
- `.eslintrc`파일에서 rule을 커스터마이징 할 수 있음

#### prettier: 코드 포맷팅 툴

- 설치: `npm install prettier --save-dev`
- `.prettierrc`파일에서 포맷팅 rule을 커스터마이징 할 수 있음

:bulb: eslint-config-prettier란?
eslint는 linting 기능을 담당하고 prettier는 formatting을 담당한다.

하지만 eslint가 formatting을 하는 경우도 있는데 이때 서로 설정이 충돌할 가능성이 있다.

따라서 eslint의 formatting 관련 rule을 모두 해제시켜주어야 한다.

`eslint-config-prettier`는 이 기능을 담당하는 eslint plugin이다.

- 설치: `npm install eslint-config-prettier --save-dev`

#### huksy: 자동으로 eslint와 prettier를 실행시켜주는 라이브러리 & git hook 설정을 도와주는 npm package

eslint와 prettier를 사용하려면 git hook을 설정해야하는데 번거로운 과정을 단축시켜준다.

- 설치: `npm install husky --save-dev`
- 처음 세팅할때만 실행: `npx husky install`
- `pointinstall`: 처음 프로젝트를 clone할때 자동으로 husky 설치

```
// package.json

{
  "scripts": {
    "postinstall": "husky install"
  },
}
```

- script 설정

```
// package.json

{
  "scripts": {
    "postinstall": "husky install",
		"format": "prettier --cache --write .",
		"lint": "eslint --cache .",
  },
}
```

- add pre-commit: `npx husky add .husky/pre-commit "npm run format"` commit할때 formatting
- add pre-push hook: `npx husky add .husky/pre-push "npm run lint"` push할때 linting

이 세가지는 전에 계속 사용했던 툴이다.

하지만 이또한 각자 사용방법이 달랐다.

나는 Husky를 쓸때 lint-staged를 함께 설치해서 썼는데 다른 방법이 있었다.

똑같이 라이브러리나 툴을 사용해도 사용방법이 다르다면 그것또한 규칙을 정해야 한다는 것을 알게되었다.

---

강의를 들으며 정말 좋았던 점은 구글링을 통해 블로그나 공식문서로 알고 있던 내용이더라도 직접 강사님이 하시는 강의를 들으면 내가 어중간하게 알고있던 점을 알게 된다는 것이다.

한마디로 알고 있다고 착각했던 점을 알게 된다.

그리고 내가 아직 초보자인 티가 났던게 무엇이냐 하면 설명을 정말 못한다는 점이다.

글로 써서 설명하는건 괜찮은데 말로 내 코드나 작업했던 방식을 설명하려니 단어가 떠오르지 않아 턱턱 막혔다.

다른 팀원들을 보면서도 참 배울 점이 많다.

단지 그냥 라이브러리나 프레임워크에 대해 아는 것이 많다고 개발을 잘하는 것은 아니다.

소프트 스킬의 중요성을 깨닫게 되는 시간이었다.
