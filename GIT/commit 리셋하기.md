# 커밋 리셋하기(reset)
리셋은 특정한 커밋으로 모든 것을 초기화 시키는 명령어 입니다.<br><br>

## 작업 내용 리셋하고 working directory로 가져오기
`git reset HEAD~n`<br>
이와 같은 명령어를 이용하면 HEAD부터 n번째에 있는 커밋들을 reset합니다.<br>
작업하던 내용은 사라지지 않고 working directory로 이동합니다.<br><br>

## 작업 내용 리셋하고 staging area로 가져오기
`git reset --soft HEAD~n`<br>
이와 같은 명령어를 이용하면 HEAD부터 n번째에 있는 커밋들을 reset합니다.<br>
작업하던 내용은 사라지지 않고 staging area로 이동합니다.<br><br>

## 작업 내용 완전히 리셋하기
`git reset --hard`<br>
 작업내용을 working directory, staging area로 가져오지 않고 완전히 리셋합니다.<br>
 포인터가 첫 번쨰 commit을 가리키는데 이 상태로 초기화 하는 것은,<br> 
 마지막으로 커밋한 이후에 수정한 모든 local의 파일들을 초기화하는 것을 뜻합니다.<br>

 ![reset](https://user-images.githubusercontent.com/56298540/180984088-6a330a32-8fbf-4b48-bc98-488d5e076078.PNG)<br>
 > working directory가 비워진 것을 확인할 수 있습니다.





