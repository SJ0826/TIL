# stash란?
working directory에서 작업 도중 깃 history에 저장하지 않고도 작업 내용을 저장해 놓을 수 있는 보관소를 뜻합니다.<br>
임시보관소로 생각하면 이해하기 편합니다.<br>

## stash stack에 파일을 push하기
`git stash`<br>
파일을 stash stack에 push합니다.<br><br>

`git stash -m "타이틀"`<br>
타이틀을 지정해 stash stack에 push합니다.<br><br>

이렇게 파일들을 stash하게 되면 working directory와 staging area에 파일이 남지 않게 됩니다.<br><br>

`git stash push -m "타이틀" --keep-indext`<br>
만약 staging area에 있는 것을 유지하면서 stash에 저장하고 싶을 때 위와 같은 명령어를 입력하면 작업하던 내용이 유지가 됩니다.<br><br>

## untracking 파일 stash하기
tracking되지 않은 파일은 자동으로 stash에 저장되지 않습니다.<br>
`git stash -u`<br>
위와 같은 명령어를 입력하면 모두다 stash stack에 들어가게 됩니다.<br><br>

## stash 이력 확인하기
`git stash list`<br>
위와 같은 명령어를 입력하면 stash stack을 확인할 수 있습니다.<br>
![stash](https://user-images.githubusercontent.com/56298540/180947440-7525351c-5dab-4eab-8ee8-53f32c9fbec4.PNG)
<br><br>

`git stash show (stash 아이디)`<br>
stash list에서 확인할 수 있는 stash아이디를 입력하면 각각 stash에서 어떤 것이 수정되었는지 확인할 수 있습니다.<br>
> 만약 powershell 사용자라면, 따옴표를 추가하여 `git stash show "(stash 아이디)"으로 입력해야합니다.<br><br>

`git stash show (stash 아이디) -p`<br>
p라는 옵션을 이용하면 더 자세한 내용을 확인할 수 있습니다.<br><br>

## stash 에서 다시 가져오기
`git stash apply`
stash stack의 가장 위에 있는 부분을 working directory에 가져옵니다.<br>
목록은 그대로 유지됩니다.<br><br>

`git stash apply (stash 아이디)`
특정한 stash를 적용하고 싶다면 stash 아이디를 지정하여 명령어를 입력해 주면 됩니다.<br><br>

`git stash branch (브랜치 이름)`
stash를 적용하면서 새로운 브랜치를 만들게 됩니다.

`git stash pop`
stash stack의 가장 위에 있는 부분을 working directory에 가져옵니다.<br>
가지고 나온 stash는 목록에서 삭제됩니다.<br><br>

## stash 삭제하기
`git stash drop (stash 아이디)`<br>
특정 stash를 삭제합니다.<br><br>

`git stash clear`<br>
전체 stash를 삭제합니다.<br><br>





