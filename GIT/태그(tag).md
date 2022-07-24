# 태그(tag)
특정한 커밋을 북마크해두고 싶을 때 유용하게 사용됩니다.<br>
   
## semantic versioning
숫자 세가지를 이용해서 major버전과 minor버전과 fix버전을 구분하여 나타냅니다.   
* major버전: 특정한 기능이 추가 되는 등 전체적인 변화가 일어났을 때 업데이트 되는 버전.    
* minor버전: 커다란 기능 중에서 조금의 기능이 업데이트 되거나 개선되었을 때 업데이트 되는 버전.   
* fix버전: 존재하는 기능 중 오류수정을 했을 때 업데이트 되는 버전.   
<br><br>

## 태그 달기 ver.1
`git tag (태그명)`   
위와 같은 명령어로 태그를 만들면 log내역을 통해서 확인 할 수 있습니다.
![tag](https://user-images.githubusercontent.com/56298540/180634917-47bcab7d-0d42-447b-87d8-cc583984a148.PNG)
<br>
<br>

## 태그 달기 ver.2
`git tag (태그명) (해쉬태그)`   
해쉬태그를 통해서 특정한 커밋에 태그를 달 수 있습니다.    
![tag2](https://user-images.githubusercontent.com/56298540/180635100-8ae009de-7f49-4706-81f7-3ad236dbd8be.PNG)
<br>
<br>

## 태그에 메세지 달기
`git tag (태그명) (해쉬태그) -am (메세지)`   
해쉬태그를 통해 특정 커밋에 메세지를 작성 할 수 있습니다.
![tag3](https://user-images.githubusercontent.com/56298540/180635403-6d4dd455-6b60-4d11-abb6-d96f214ecddf.PNG)   
`git show`를 이용해 확인할 수 있습니다.   
![tag4](https://user-images.githubusercontent.com/56298540/180635404-b125399a-fe93-4af6-898e-e4620a2f0246.PNG)
<br>
<br>

## 태그 검색하기
`git tag -l "문자열"`   
특정 문자열이 들어있는 모든 태그를 검색 할 수 있습니다.   
<br><br>

## 태그 삭제하기
`git tag -d (태그명)`   
아래와 같이 태그를 삭제할 수 있습니다.   
![tag5](https://user-images.githubusercontent.com/56298540/180635962-fd7bf024-f800-472f-abf1-8c0bb6860c71.PNG)

## 새로운 브랜치에 태그 생성하기
`git checkout -b (브랜치 이름) (태그명)`   
새로운 브랜치를 생성하여 태그를 만들어줍니다.   
![tag6](https://user-images.githubusercontent.com/56298540/180636069-fd7fca64-dc2b-420b-b70c-b0b51cd96199.PNG)
<br><br>

