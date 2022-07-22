# 버전들 목록 보기 log

## git log

<git log를 통해 확인할 수 있는 것>
* commit 아이디   
* 작성자   
* commit 시간
* 타이틀   

![git-log](https://user-images.githubusercontent.com/56298540/180410143-bd3c9142-5458-4443-982d-316b193a1cf3.PNG)
    
## git log -p
patch 옵션을 사용하면 수정된 파일의 내용들도 확인할 수 있습니다.   
![git log -p](https://user-images.githubusercontent.com/56298540/180411460-3412e18e-9079-4620-a136-4a6bd0cbc193.PNG)

## git log oneline
해쉬코드의 앞자리 문자열과 간단한 커밋메세지를 간단하게 확인할 수 있습니다.   
![git log --oneline](https://user-images.githubusercontent.com/56298540/180411818-fdfe6e29-46f5-4774-8207-cd965cf6b838.PNG)
   
---

## HEAD란?
파일을 commit할 때, 현재 commit한 파일은 이전 commit한 파일을 참조합니다.   
a b c d 순으로 commit한다고 가정할 때, b는 a를 가리키고 c는 b를 가리킵니다.   
이런식으로 commit을 해 나가는 기본 줄기를 master branch 라고 합니다.
> a <- b<- c<- d (시각적 표현)   

이 master brach에서 HEAD는 마지막으로 commit한 d파일을 가리키게 됩니다.   
이때 c는 head~1이 되어 head가 있는 곳에서 첫 번째 부모임을 설명합니다.   
b도 마찬가지로 head~2가 됩니다.   
   
만약, b로 돌아가고 싶다면   
``` 
git checkout b해쉬태그
```
를 입력하여 b로 돌아갈 수 있습니다.   
![git checkout](https://user-images.githubusercontent.com/56298540/180416896-3faceac3-222d-4340-9c7d-0ded87a32286.PNG)

```
git checkout master
```
위와 같이 입력하면 다시 원상태로 돌아옵니다.
