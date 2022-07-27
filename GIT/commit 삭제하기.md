# commit 삭제하기

1. 히스토리 내역에 삭제하기를 원하는 커밋을 확인합니다.<br><br>

2. `git rebase -i (해쉬코드 또는 HEAD~n)`<br>
rebase 명령어를 이용해 해당 커밋까지의 내역을 수정하는 창을 띄웁니다.<br><br>

3. 삭제를 원하는 커밋에 d(drop)옵션을 입력합니다.<br>
이렇게 되면 삭제된 파일의 다음 커밋에서 수정사항이 발생했기 때문에 conflict가 생기게 됩니다.<br>
![rebase4](https://user-images.githubusercontent.com/56298540/181232428-f8461915-7c46-434a-a50d-b32cc0d3d3e3.PNG)<br>

4. `git status`를 입력해 상태를 확인해보면, 다음과 같이 출력된 것을 확인할 수 있습니다.<br>
![rebase5](https://user-images.githubusercontent.com/56298540/181232803-334bfa8e-c428-404a-8472-1a749a10aa81.PNG)<br>
> interactive rebase가 진행중인데 payment-ui.txt(삭제된 커밋 다음 커밋의 파일)이 삭제되었다.

5. `git add . `를 통해 삭제된 파일을 다시 추가합니다.<br><br>

5. `git rebase --continue`를 통해 rebase를 계속 진행합니다.<br><br>

4. 히스토리 내역을 확인하면 해당 커밋이 삭제된 것을 확인 할 수 있습니다.

