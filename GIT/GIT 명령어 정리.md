# GIT 명령어 정리

```
git status
```
파일 정보를 확인할 수 있습니다. <br>
```
git status -s
```
파일 정보를 더 간단히 확인 할 수 있습니다.<br>
```
git init
```
깃을 초기화 합니다.<br>
깃을 초기화하면 commit해서 버전을 관리하는 master branch가 생성이 됩니다.<br>
**open .git(start .git)**을 입력하여 깃폴더가 생성된 것을 확인할 수 있습니다.<br><br>

```
git rm (파일)
```
원격저장소와 로컬저장소의 파일을 삭제합니다.<br>
더이상 깃 프로젝트로 활용하지 않습니다.<br>

```
git rm --cached (파일)
```
원격저장소에 있는 파일을 삭제합니다.<br>
로컬저장소에 있는 파일은 삭제하지 않습니다.<br>

```
git add (파일)
```
untracking 파일을 staging area에 추가합니다.<br>
이로써 staging area에 추가된 파일은 commit할 준비가 되었습니다.<br>

``` 
git echo (파일) >> .gitignore
```
특정 파일을 버전관리에서 제외시킵니다.<br>
```
git diff
```
commit이나 branch 사이의 다른 점 혹은 파일이나 repository와 working directory 사이의 다른 점을 보여줍니다.<br>
즉, 수정된 파일의 내용을 상세히 확인할 수 있습니다.<br>
```
git diff --staged
```
staging area에 있는 파일의 수정 내용을 확인할 수 있습니다.<br>
```
git commit
```
commit은 로컬 저장소에 코드 변경 이력을 남기기 위한 작업입니다.<br>
staging area에 있는 파일들을 원격 저장소에 업로드할 준비를 합니다.

---
commit 할때 팁!
1. 변경내용을 commit할 때는 해당내용만 변경하여 commit message에 작성한다.<br>
2. commit은 너무 커도 문제가 되지만, 너무 작아도 적합하지 않다. 적당한 크기는 프로젝트를 진행하면서 감을 익힌다.