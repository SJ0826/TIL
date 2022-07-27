# 커밋 분할하기

개발자들과 협업을 할 때는 하나의 커밋에는 하나의 내용이 있어야 합니다.<br><br>

너무 많은 내용을 커밋하게 되었을 때는 커밋을 분할해야 합니다.<br><br>

## 순서

### 1. `git rebase -i 해쉬코드 또는 HEAD~n` <br>
위와 같은 명령어를 입력하여 분할해야하는 커밋을 수정하기 위해 에디터를 띄웁니다.<br><br>

에디터에서 해당 커밋의 명령어를 e(edit)로 고칩니다.<br><br>

저장 후 히스토리 내역을 확인하면 HEAD가 해당 커밋으로 이동한 것을 확인할 수 있습니다.<br>
![commit](https://user-images.githubusercontent.com/56298540/181237630-1627d3ec-0b04-4a26-8fb0-dc24ca0bf366.PNG)<br><br>

### 2. `git reset`<br>
명령어를 입력해 해당 커밋을 리셋시켜 파일을 working directory로 가져옵니다.<br><br>

![commit2](https://user-images.githubusercontent.com/56298540/181238046-df16b4d9-64bc-40cd-b70d-198579690c67.PNG)<br>

`git status`를 입력해 확인해 보면 rebase가 진행중이며 두개의 파일이 working directory로 온 것을 확인할 수 있습니다.<br><br>

### 3. 각각 파일 하나씩 다시 커밋하기

파일들을 하나씩 staging area에 추가하고 다시 커밋합니다.<br><br>

### 4. `git rebase --continue`
명령어를 입력해 rebase를 진행합니다.<br><br>

![commit3](https://user-images.githubusercontent.com/56298540/181238778-7d7827af-af04-4133-8024-b55e8233426c.PNG)

이렇게 커밋이 분할 된 것을 확인할 수 있습니다.

## 참조
* [더 북] https://thebook.io/080212/<br>
* [강 의] 드림코딩
