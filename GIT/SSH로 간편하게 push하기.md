# SSH로 간편하게 push하기

## SSH란?
Secure SHell protocol의 약자로 터미널과 서버간에 안전하게 아이디와 비밀번호를 유지해주는 방법입니다.<br><br>

서버에는 public key를 생성하고 사용자의 컴퓨터에는 private key를 생성해 넣음으로써 push를 할 때 번거롭게 아이디와 비밀번호를 입력하지 않아도 됩니다.<br><br>

## 순서

### 1. 깃허브 페이지에서 setting > SSH keys and GPS keys 로 이동

![github](https://user-images.githubusercontent.com/56298540/181246239-208fe5c9-0dca-4c45-bb71-5c5f25dcfb3d.PNG)<br>
아직 등록된 SSH key가 없는 것을 확인할 수 있습니다.<br><br>

### 2. Git Bash 열기

### 3. 키 생성하기
`$ ssh-keygen -t ed25519 -C "your_email@example.com"`<br><br>
다음과 같은 명령어를 입력하면 키를 생성한다는 메세지가 출력됩니다.<br><br>
혹시 본인의 이메일을 잊었다면 `git config --list`를 통해 확인 가능합니다.<br><br>
키가 저장될 경로를 확인 후 비밀번호를 설정하지 않는다면, 'ENTER'를 두번 입력합니다.<br><br>
![key](https://user-images.githubusercontent.com/56298540/181249516-48668e65-7a74-4bf9-96f6-94f3a4e28578.PNG)<br>
출력된 메세지를 확인해보면 public key와 private key가 어느 폴더에 저장되었는지 확인할 수 있습니다.<br><br>

### 4. 키 설정하기
저장된 public key를 복사해서 git hub페이지로 돌아가 설정합니다.<br><br>

이렇게 커밋을 할때마다 아이디와 비밀번호를 입력하지 않고 검증된 유저로 커밋을 할 수 있게 되었습니다.
