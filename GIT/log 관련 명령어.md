# log 관련 명령어.md


`git log -3`

> 최근 히스토리 3개를 보여줍니다.<br>
   
`git log --author="sujin"`<br>
> sujin이라는 이름의 사용자가 커밋한 히스토리를 보여줍니다.    
   
`git log --before="2020-07-24"`<br>
>2020-07-24 이전의 커밋한 히스토리를 보여줍니다.<br>
   
`git log --grep="project"`   
> project가 들어간 커밋 타이틀을 보여줍니다.<br>
    
`git log -S "about"`   
> 커밋 내용에 about이 들어간 히스토리를 보여줍니다.<br>

`git log about.txt`   
> about.txt에 해당하는 히스토리를 볼 수 있습니다.<br>
    
`git log -p "about.txt"`<br>
>about.txt.에 해당하는 좀 더 자세한 히스토리를 볼 수 있습니다.<br>
   
`git log HEAD~1`<br>
> git log의 HEAD에서 이전 부모부터 히스토리를 볼 수 있습니다.<br>
   
`git show (해당 해쉬코드)`<br>
> 해당하는 커밋의 내용을 볼 수 있습니다.
   
`git diff (해쉬코드1) (해쉬코드2)`<br>
> 두가지 커밋 내용을 비교하며 내용을 확인 할 수 있습니다.



