# commit전 취소하기

## working directory에 있는 파일 수정 취소하기(초기화 하기)

`git restore .`<br>
working directory에 있는 전체 파일을 초기화 합니다.<br><br>

`git restore (파일 이름)`<br>
working directory에 있는 특정 파일을 초기화 합니다.<br><br>

`git restore --source=(해쉬코드 또는 HEAD~n) (파일명)`
파일에 대해서 특정커밋 이전 상태로 초기화 합니다.<br><br>

## staging area에 있는 파일 수정 취소하기(초기화 하기)

`git restore --staged .`
staging area에 있는 전체 파일을 초기화 합니다.<br><br>

`git restore --staged (파일 이름)`
staging area에 있는 특정 파일을 초기화 합니다.<br><br>

---
WIP(Working In Progress): 아직 작업이 진행 중인 것을 뜻합니다.<br><br>


