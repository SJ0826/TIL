# git pull 명령 오류<br>The following untracked working tree files would be overwritten by merge
git 저장소에서 파일을 당겨 오늰데 오류가 발생했다.
```
error: The following untracked working tree files would be overwritten by merge:
오류 발생한 파일 위치 및 이름
Please move or remove them before you can merge.
Aborting
```
<br>
깔끔하게 하고 싶어서 자꾸 이것저것 해서 그런가 overwritten 됐단다.<br>
역시나 하라는 대로 해준다.
```
git clean -d -f -f
```
하고 다시 git pull 해주면<br>

빠른 해결~


 