# 리베이스(Rebase)

리베이스는 파생된 브랜체의 기준이 되는 베이스 커밋을 변경하는 것입니다.<br>
파생된 브랜치를 master 브랜치의 최신 버전으로 포인터를 옮겨주는 것, 이것을 리베이스(rebase)라고 합니다.<br><br>

## 주의할 점!<br>
다른 개발자와 함께 파생된 브랜치에서 작업을 할 경우, 다른 커밋이 생기기 때문에 리베이스를 하면 merge conflict이 발생할 수 있습니다.<br>
그러므로 서버에 업로드된 히스토리는 절대 리베이스하면 안됩니다<br><br>

## 순서

1. `git checkout (파생된 브랜치)`를 이용해 파생된 브랜치로 이동합니다.<br><br>

2. `git rebase master`를 입력해 master 브랜치의 최신버전으로 포인터를 이동시킵니다.
![rebase](https://user-images.githubusercontent.com/56298540/180745027-ba6ece98-c3ce-4118-9613-4c149866c275.PNG)<br>

3. `git merge (파생된 브랜치)`를 이용하면 merge가 가능한 것을 확인할 수 있습니다.<br><br>

4. 이후 `git branch -d (브랜치명)`을 입력해 쓸모 없어진 브랜치를 삭제해 깔끔하게 정리해 줍니다.

## rebase --onto

파생된 브랜치에서 다시 파생된 브랜치의 포인터를 master 브랜치에 옮겨주는 것을 뜻합니다.<br>
이때 `rebase --onto`옵션을 사용합니다.
![rebase2](https://user-images.githubusercontent.com/56298540/180751859-f5ce5618-855c-44ca-9b63-9d61b0c5dd79.PNG)<br>
위와 같이 포인터를 옮겨 준 후, merge를 하면 성공적으로 merge된 것을 확인할 수 있습니다.
